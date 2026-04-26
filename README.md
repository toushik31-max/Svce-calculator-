# Svce-calculator-<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>SVCE Calculator</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
    <script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
    <script>
        window.MathJax = {
            tex: {
                inlineMath: [['$', '$'], ['\\(', '\\)']],
                displayMath: [['$$', '$$'], ['\\[', '\\]']]
            }
        };
    </script>
</head>
<body class="bg-gradient-to-br from-indigo-100 via-purple-50 to-pink-100 min-h-screen relative overflow-x-hidden">
    <!-- Background decorative elements -->
    <div class="absolute inset-0 overflow-hidden pointer-events-none">
        <div class="absolute -top-40 -right-40 w-80 h-80 bg-gradient-to-br from-blue-400/30 to-indigo-600/40 rounded-full blur-3xl animate-pulse"></div>
        <div class="absolute -bottom-40 -left-40 w-80 h-80 bg-gradient-to-tr from-purple-400/30 to-pink-600/40 rounded-full blur-3xl animate-pulse" style="animation-delay: 1s"></div>
        <div class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 w-96 h-96 bg-gradient-to-r from-indigo-400/20 to-purple-400/30 rounded-full blur-3xl animate-pulse" style="animation-delay: 2s"></div>
        <div class="absolute top-20 left-20 w-32 h-32 bg-gradient-to-br from-cyan-300/25 to-blue-500/35 rounded-full blur-2xl animate-bounce" style="animation-duration: 3s"></div>
        <div class="absolute top-40 right-32 w-24 h-24 bg-gradient-to-br from-emerald-300/30 to-teal-500/40 rounded-full blur-2xl animate-bounce" style="animation-duration: 4s; animation-delay: 0.5s"></div>
        <div class="absolute bottom-32 left-1/3 w-40 h-40 bg-gradient-to-br from-rose-300/25 to-pink-500/35 rounded-full blur-2xl animate-bounce" style="animation-duration: 5s; animation-delay: 1s"></div>
        <div class="absolute bottom-20 right-20 w-28 h-28 bg-gradient-to-br from-amber-300/30 to-orange-500/40 rounded-full blur-2xl animate-bounce" style="animation-duration: 3.5s; animation-delay: 1.5s"></div>
        <div class="absolute top-1/4 left-1/4 w-16 h-16 bg-gradient-to-br from-violet-400/20 to-purple-600/30 transform rotate-45 blur-xl animate-spin" style="animation-duration: 20s"></div>
        <div class="absolute top-3/4 right-1/4 w-12 h-12 bg-gradient-to-br from-sky-400/25 to-blue-600/35 transform rotate-12 blur-xl animate-spin" style="animation-duration: 15s; animation-direction: reverse"></div>
        <div class="absolute inset-0 opacity-5">
            <div class="w-full h-full" style="background-image: radial-gradient(circle at 1px 1px, rgba(99, 102, 241, 0.3) 1px, transparent 0); background-size: 20px 20px;"></div>
        </div>
    </div>
    <div class="container mx-auto px-4 py-8 relative z-10 max-w-5xl">
        <!-- Header -->
        <div class="text-center mb-12 animate-fade-in max-w-md mx-auto">
            <div class="inline-block p-4 bg-white/80 backdrop-blur-sm rounded-2xl shadow-lg mb-4">
                <h1 class="text-5xl font-bold bg-gradient-to-r from-indigo-600 via-purple-600 to-blue-600 bg-clip-text text-transparent mb-2">SVCE Calculator</h1>
                <p class="text-gray-700 text-lg font-medium">Calculate your SGPA, CGPA, and Theory Marks</p>
            </div>
            <div class="flex justify-center space-x-2 mt-4">
                <div class="w-2 h-2 bg-indigo-400 rounded-full animate-bounce"></div>
                <div class="w-2 h-2 bg-purple-400 rounded-full animate-bounce" style="animation-delay: 0.1s"></div>
                <div class="w-2 h-2 bg-blue-400 rounded-full animate-bounce" style="animation-delay: 0.2s"></div>
            </div>
        </div>

        <!-- Tab Navigation -->
        <div class="flex justify-center mb-12 overflow-x-auto">
            <div class="bg-white/90 backdrop-blur-md rounded-2xl p-2 shadow-xl border border-white/20 min-w-max whitespace-nowrap flex space-x-1">
                <button onclick="showTab('theory')" id="theoryTab" class="px-6 py-3 rounded-xl bg-gradient-to-r from-indigo-600 to-purple-600 text-white font-semibold transition-all duration-300 transform hover:scale-105 shadow-lg whitespace-nowrap">Theory Marks</button>
                <button onclick="showTab('lab')" id="labTab" class="px-6 py-3 rounded-xl text-indigo-600 hover:bg-gradient-to-r hover:from-indigo-50 hover:to-purple-50 font-semibold transition-all duration-300 transform hover:scale-105 whitespace-nowrap">Lab Marks</button>
                <button onclick="showTab('theoryCumPractical')" id="theoryCumPracticalTab" class="px-6 py-3 rounded-xl text-indigo-600 hover:bg-gradient-to-r hover:from-indigo-50 hover:to-purple-50 font-semibold transition-all duration-300 transform hover:scale-105 whitespace-nowrap">Theory cum Practical</button>
                <button onclick="showTab('gpa')" id="gpaTab" class="px-6 py-3 rounded-xl text-indigo-600 hover:bg-gradient-to-r hover:from-indigo-50 hover:to-purple-50 font-semibold transition-all duration-300 transform hover:scale-105 whitespace-nowrap">GPA Calculator</button>
                <button onclick="showTab('cgpa')" id="cgpaTab" class="px-6 py-3 rounded-xl text-indigo-600 hover:bg-gradient-to-r hover:from-indigo-50 hover:to-purple-50 font-semibold transition-all duration-300 transform hover:scale-105 whitespace-nowrap">CGPA Calculator</button>
            </div>
        </div>

        <!-- Theory Marks Section -->
        <div id="theorySection" class="max-w-4xl mx-auto">
            <div class="bg-white/95 backdrop-blur-sm rounded-3xl shadow-2xl p-8 mb-8 border border-white/20 hover:shadow-3xl transition-all duration-500 transform hover:-translate-y-1">
                <div class="flex items-center mb-8">
                    <div class="w-1 h-8 bg-gradient-to-b from-indigo-500 to-purple-500 rounded-full mr-4"></div>
                    <h2 class="text-3xl font-bold bg-gradient-to-r from-indigo-600 to-purple-600 bg-clip-text text-transparent">Theory Mark Calculation</h2>
                </div>
                <div class="grid md:grid-cols-3 gap-6 mb-8">
                    <div class="bg-gradient-to-br from-gray-50 to-gray-100/50 p-6 rounded-2xl border border-gray-200/50 hover:shadow-lg transition-all duration-300 transform hover:-translate-y-1">
                        <h3 class="text-lg font-semibold text-gray-700 mb-4">FAT 1</h3>
                        <div class="space-y-3">
                            <div>
                                <label class="block text-sm font-medium text-gray-600 mb-1">Test Score (out of 50)</label>
                                <input type="number" id="fat1Test" max="50" min="0" class="w-full px-4 py-3 border border-gray-300 rounded-xl focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:border-transparent transition-all duration-300 bg-white/80 backdrop-blur-sm hover:shadow-md" placeholder="Enter test score" oninput="calculateFAT()">
                            </div>
                            <div>
                                <label class="block text-sm font-medium text-gray-600 mb-1">Assignment Score (out of 50)</label>
                                <input type="number" id="fat1Asg" max="50" min="0" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Enter assignment score" oninput="calculateFAT()">
                            </div>
                            <div class="text-sm text-gray-500">FAT 1 Score: <span id="fat1Result" class="font-semibold">-</span></div>
                        </div>
                    </div>
                    <div class="bg-gradient-to-br from-gray-50 to-gray-100/50 p-6 rounded-2xl border border-gray-200/50 hover:shadow-lg transition-all duration-300 transform hover:-translate-y-1">
                        <h3 class="text-lg font-semibold text-gray-700 mb-4">FAT 2</h3>
                        <div class="space-y-3">
                            <div>
                                <label class="block text-sm font-medium text-gray-600 mb-1">Test Score (out of 50)</label>
                                <input type="number" id="fat2Test" max="50" min="0" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Enter test score" oninput="calculateFAT()">
                            </div>
                            <div>
                                <label class="block text-sm font-medium text-gray-600 mb-1">Assignment Score (out of 50)</label>
                                <input type="number" id="fat2Asg" max="50" min="0" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Enter assignment score" oninput="calculateFAT()">
                            </div>
                            <div class="text-sm text-gray-500">FAT 2 Score: <span id="fat2Result" class="font-semibold">-</span></div>
                        </div>
                    </div>
                    <div class="bg-gradient-to-br from-gray-50 to-gray-100/50 p-6 rounded-2xl border border-gray-200/50 hover:shadow-lg transition-all duration-300 transform hover:-translate-y-1">
                        <h3 class="text-lg font-semibold text-gray-700 mb-4">FAT 3</h3>
                        <div class="space-y-3">
                            <div>
                                <label class="block text-sm font-medium text-gray-600 mb-1">Test Score (out of 50)</label>
                                <input type="number" id="fat3Test" max="50" min="0" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Enter test score" oninput="calculateFAT()">
                            </div>
                            <div>
                                <label class="block text-sm font-medium text-gray-600 mb-1">Assignment Score (out of 50)</label>
                                <input type="number" id="fat3Asg" max="50" min="0" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Enter assignment score" oninput="calculateFAT()">
                            </div>
                            <div class="text-sm text-gray-500">FAT 3 Score: <span id="fat3Result" class="font-semibold">-</span></div>
                        </div>
                    </div>
                </div>
                <div class="bg-gray-50 p-6 rounded-lg mb-8">
                    <h3 class="text-lg font-semibold text-gray-700 mb-4">End Semester Exam</h3>
                    <div class="space-y-3">
                        <div>
                            <label class="block text-sm font-medium text-gray-600 mb-1">End Semester Score (out of 100)</label>
                            <input type="number" id="endSemScore" max="100" min="0" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Enter end semester score" oninput="calculateFAT()">
                        </div>
                        <div class="text-sm text-gray-500">End Semester: <span id="endSemResult" class="font-semibold">-</span></div>
                    </div>
                </div>
                <div class="space-y-4">
                    <div class="bg-gradient-to-r from-blue-50 to-indigo-50 p-6 rounded-2xl border border-blue-200/50 shadow-lg">
                        <h3 class="text-lg font-bold text-blue-800 mb-2 flex items-center">
                            <div class="w-2 h-2 bg-blue-500 rounded-full mr-2"></div>
                            Internal Assessment
                        </h3>
                        <div class="text-lg">
                            <span class="text-gray-700">Internal Average: </span>
                            <span id="internalAvgResult" class="font-bold text-blue-600 text-xl">-</span>
                            <span class="text-gray-500"> / 40</span>
                        </div>
                    </div>
                    <div class="bg-gradient-to-r from-indigo-50 to-purple-50 p-8 rounded-2xl border border-indigo-200/50 shadow-xl">
                        <h3 class="text-xl font-bold text-indigo-800 mb-4 flex items-center">
                            <div class="w-3 h-3 bg-gradient-to-r from-indigo-500 to-purple-500 rounded-full mr-3"></div>
                            Final Theory Mark
                        </h3>
                        <div class="text-lg mb-4">
                            <span class="text-gray-700">Theory Mark: </span>
                            <span id="finalTheoryMark" class="font-bold text-indigo-600 text-3xl">-</span>
                            <span class="text-gray-500 text-xl"> / 100</span>
                        </div>
                        <div class="mt-4">
                            <span id="theoryPassFail" class="px-6 py-3 rounded-full text-sm font-bold shadow-lg">-</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Theory cum Practical Calculator -->
        <div id="theoryCumPracticalSection" class="max-w-4xl mx-auto hidden">
            <div class="bg-white/95 backdrop-blur-sm rounded-3xl shadow-2xl p-8 mb-8 border border-white/20 hover:shadow-3xl transition-all duration-500 transform hover:-translate-y-1">
                <div class="flex items-center mb-8">
                    <div class="w-1 h-8 bg-gradient-to-b from-indigo-500 to-purple-500 rounded-full mr-4"></div>
                    <h2 class="text-3xl font-bold bg-gradient-to-r from-indigo-600 to-purple-600 bg-clip-text text-transparent">Theory cum Practical Mark Calculation</h2>
                </div>
                <div class="mb-8">
                    <h3 class="text-xl font-semibold text-gray-700 mb-6">Internal Assessment (50 marks)</h3>
                    <div class="grid md:grid-cols-3 gap-6 mb-6">
                        <div class="bg-gradient-to-br from-gray-50 to-gray-100/50 p-6 rounded-2xl border border-gray-200/50 hover:shadow-lg transition-all duration-300 transform hover:-translate-y-1">
                            <h4 class="text-lg font-semibold text-gray-700 mb-4">CAT 1</h4>
                            <div>
                                <label class="block text-sm font-medium text-gray-600 mb-1">CAT 1 Score (out of 50)</label>
                                <input type="number" id="tcpCat1Score" max="50" min="0" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Enter CAT 1 score" oninput="calculateTCP()">
                            </div>
                        </div>
                        <div class="bg-gradient-to-br from-gray-50 to-gray-100/50 p-6 rounded-2xl border border-gray-200/50 hover:shadow-lg transition-all duration-300 transform hover:-translate-y-1">
                            <h4 class="text-lg font-semibold text-gray-700 mb-4">CAT 2</h4>
                            <div>
                                <label class="block text-sm font-medium text-gray-600 mb-1">CAT 2 Score (out of 50)</label>
                                <input type="number" id="tcpCat2Score" max="50" min="0" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Enter CAT 2 score" oninput="calculateTCP()">
                            </div>
                        </div>
                        <div class="bg-gradient-to-br from-gray-50 to-gray-100/50 p-6 rounded-2xl border border-gray-200/50 hover:shadow-lg transition-all duration-300 transform hover:-translate-y-1">
                            <h4 class="text-lg font-semibold text-gray-700 mb-4">Model Exam (CAT 3)</h4>
                            <div>
                                <label class="block text-sm font-medium text-gray-600 mb-1">Model Exam Score (out of 50)</label>
                                <input type="number" id="tcpModelScore" max="50" min="0" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Enter model exam score" oninput="calculateTCP()">
                            </div>
                        </div>
                    </div>
                    <div class="bg-gray-50 p-6 rounded-lg mb-6">
                        <h4 class="text-lg font-semibold text-gray-700 mb-4">Assignments</h4>
                        <div class="grid md:grid-cols-3 gap-4">
                            <div>
                                <label class="block text-sm font-medium text-gray-600 mb-1">Assignment 1 (out of 50)</label>
                                <input type="number" id="tcpAssignment1Score" max="50" min="0" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Enter assignment 1 score" oninput="calculateTCP()">
                            </div>
                            <div>
                                <label class="block text-sm font-medium text-gray-600 mb-1">Assignment 2 (out of 50)</label>
                                <input type="number" id="tcpAssignment2Score" max="50" min="0" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Enter assignment 2 score" oninput="calculateTCP()">
                            </div>
                            <div>
                                <label class="block text-sm font-medium text-gray-600 mb-1">Assignment 3 (out of 50)</label>
                                <input type="number" id="tcpAssignment3Score" max="50" min="0" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Enter assignment 3 score" oninput="calculateTCP()">
                            </div>
                        </div>
                    </div>
                    <div class="space-y-4">
                        <div class="bg-blue-50 p-4 rounded-lg">
                            <div class="text-lg font-bold text-blue-800">Total Internal: <span id="tcpTotalInternal" class="text-xl">-</span> / 50</div>
                        </div>
                    </div>
                </div>
                <div class="mb-8">
                    <h3 class="text-xl font-semibold text-gray-700 mb-6">External Assessment (100 marks)</h3>
                    <div class="grid md:grid-cols-2 gap-6 mb-6">
                        <div class="bg-gradient-to-br from-gray-50 to-gray-100/50 p-6 rounded-2xl border border-gray-200/50 hover:shadow-lg transition-all duration-300 transform hover:-translate-y-1">
                            <h4 class="text-lg font-semibold text-gray-700 mb-4">Semester Practical Exam</h4>
                            <div>
                                <label class="block text-sm font-medium text-gray-600 mb-1">Practical Score (out of 40)</label>
                                <input type="number" id="tcpPracticalScore" max="40" min="0" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Enter practical score" oninput="calculateTCP()">
                            </div>
                        </div>
                        <div class="bg-gradient-to-br from-gray-50 to-gray-100/50 p-6 rounded-2xl border border-gray-200/50 hover:shadow-lg transition-all duration-300 transform hover:-translate-y-1">
                            <h4 class="text-lg font-semibold text-gray-700 mb-4">Semester Theory Exam</h4>
                            <div>
                                <label class="block text-sm font-medium text-gray-600 mb-1">Theory Score (out of 60)</label>
                                <input type="number" id="tcpTheoryScore" max="60" min="0" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Enter theory score" oninput="calculateTCP()">
                            </div>
                        </div>
                    </div>
                </div>
                <div class="bg-indigo-50 p-6 rounded-lg">
                    <h3 class="text-xl font-bold text-indigo-800 mb-2">Final Theory cum Practical Mark</h3>
                    <div class="text-lg">
                        <span class="text-gray-700">Total Mark: </span>
                        <span id="tcpFinalMark" class="font-bold text-indigo-600 text-2xl">-</span>
                        <span class="text-gray-500"> / 100</span>
                    </div>
                    <div class="mt-4">
                        <span id="tcpPassFail" class="px-4 py-2 rounded-full text-sm font-bold">-</span>
                    </div>
                </div>
            </div>
        </div>

        <!-- Lab Marks Section -->
        <div id="labSection" class="max-w-4xl mx-auto hidden">
            <div class="bg-white/95 backdrop-blur-sm rounded-3xl shadow-2xl p-8 mb-8 border border-white/20 hover:shadow-3xl transition-all duration-500 transform hover:-translate-y-1">
                <div class="flex items-center mb-8">
                    <div class="w-1 h-8 bg-gradient-to-b from-indigo-500 to-purple-500 rounded-full mr-4"></div>
                    <h2 class="text-3xl font-bold bg-gradient-to-r from-indigo-600 to-purple-600 bg-clip-text text-transparent">Lab Mark Calculation</h2>
                </div>
                <div class="grid md:grid-cols-3 gap-6 mb-8">
                    <div class="bg-gradient-to-br from-gray-50 to-gray-100/50 p-6 rounded-2xl border border-gray-200/50 hover:shadow-lg transition-all duration-300 transform hover:-translate-y-1">
                        <h3 class="text-lg font-semibold text-gray-700 mb-4">CAT 1</h3>
                        <div class="space-y-3">
                            <div>
                                <label class="block text-sm font-medium text-gray-600 mb-1">CAT 1 Score (out of 50)</label>
                                <input type="number" id="cat1Score" max="50" min="0" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Enter CAT 1 score" oninput="calculateLab()">
                            </div>
                            <div class="text-sm text-gray-500">CAT 1: <span id="cat1Result" class="font-semibold">-</span></div>
                        </div>
                    </div>
                    <div class="bg-gradient-to-br from-gray-50 to-gray-100/50 p-6 rounded-2xl border border-gray-200/50 hover:shadow-lg transition-all duration-300 transform hover:-translate-y-1">
                        <h3 class="text-lg font-semibold text-gray-700 mb-4">CAT 2</h3>
                        <div class="space-y-3">
                            <div>
                                <label class="block text-sm font-medium text-gray-600 mb-1">CAT 2 Score (out of 50)</label>
                                <input type="number" id="cat2Score" max="50" min="0" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Enter CAT 2 score" oninput="calculateLab()">
                            </div>
                            <div class="text-sm text-gray-500">CAT 2: <span id="cat2Result" class="font-semibold">-</span></div>
                        </div>
                    </div>
                    <div class="bg-gradient-to-br from-gray-50 to-gray-100/50 p-6 rounded-2xl border border-gray-200/50 hover:shadow-lg transition-all duration-300 transform hover:-translate-y-1">
                        <h3 class="text-lg font-semibold text-gray-700 mb-4">CAT 3</h3>
                        <div class="space-y-3">
                            <div>
                                <label class="block text-sm font-medium text-gray-600 mb-1">CAT 3 Score (out of 50)</label>
                                <input type="number" id="cat3Score" max="50" min="0" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Enter CAT 3 score" oninput="calculateLab()">
                            </div>
                            <div class="text-sm text-gray-500">CAT 3: <span id="cat3Result" class="font-semibold">-</span></div>
                        </div>
                    </div>
                </div>
                <div class="grid md:grid-cols-2 gap-6 mb-8">
                    <div class="bg-gradient-to-br from-gray-50 to-gray-100/50 p-6 rounded-2xl border border-gray-200/50 hover:shadow-lg transition-all duration-300 transform hover:-translate-y-1">
                        <h3 class="text-lg font-semibold text-gray-700 mb-4">Model Exam</h3>
                        <div class="space-y-3">
                            <div>
                                <label class="block text-sm font-medium text-gray-600 mb-1">Model Exam Score (out of 100)</label>
                                <input type="number" id="modelExamScore" max="100" min="0" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Enter model exam score" oninput="calculateLab()">
                            </div>
                            <div class="text-sm text-gray-500">Model Exam: <span id="modelExamResult" class="font-semibold">-</span></div>
                        </div>
                    </div>
                    <div class="bg-gradient-to-br from-gray-50 to-gray-100/50 p-6 rounded-2xl border border-gray-200/50 hover:shadow-lg transition-all duration-300 transform hover:-translate-y-1">
                        <h3 class="text-lg font-semibold text-gray-700 mb-4">End Semester Lab Exam</h3>
                        <div class="space-y-3">
                            <div>
                                <label class="block text-sm font-medium text-gray-600 mb-1">End Semester Score (out of 100)</label>
                                <input type="number" id="endSemesterScore" max="100" min="0" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Enter end semester score" oninput="calculateLab()">
                            </div>
                            <div class="text-sm text-gray-500">End Semester: <span id="endSemesterResult" class="font-semibold">-</span></div>
                        </div>
                    </div>
                </div>
                <div class="space-y-4">
                    <div class="bg-blue-50 p-6 rounded-lg">
                        <h3 class="text-lg font-bold text-blue-800 mb-2">Internal Assessment</h3>
                        <div class="text-lg">
                            <span class="text-gray-700">Internal Mark: </span>
                            <span id="internalMark" class="font-bold text-blue-600 text-xl">-</span>
                            <span class="text-gray-500"> / 60</span>
                        </div>
                    </div>
                    <div class="bg-indigo-50 p-6 rounded-lg">
                        <h3 class="text-xl font-bold text-indigo-800 mb-2">Final Lab Mark</h3>
                        <div class="text-lg">
                            <span class="text-gray-700">Lab Mark: </span>
                            <span id="finalLabMark" class="font-bold text-indigo-600 text-2xl">-</span>
                            <span class="text-gray-500"> / 100</span>
                        </div>
                        <div class="mt-4">
                            <span id="labPassFail" class="px-4 py-2 rounded-full text-sm font-bold">-</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- GPA Calculator Section -->
        <div id="gpaSection" class="max-w-4xl mx-auto hidden">
            <div class="bg-white/95 backdrop-blur-sm rounded-3xl shadow-2xl p-8 mb-8 border border-white/20 hover:shadow-3xl transition-all duration-500 transform hover:-translate-y-1">
                <div class="flex items-center mb-8">
                    <div class="w-1 h-8 bg-gradient-to-b from-indigo-500 to-purple-500 rounded-full mr-4"></div>
                    <h2 class="text-3xl font-bold bg-gradient-to-r from-indigo-600 to-purple-600 bg-clip-text text-transparent">GPA Calculator</h2>
                </div>
                <div class="mb-6">
                    <button onclick="addSubject()" class="bg-gradient-to-r from-indigo-600 to-purple-600 text-white px-6 py-3 rounded-xl hover:from-indigo-700 hover:to-purple-700 transition-all duration-300 transform hover:scale-105 shadow-lg hover:shadow-xl font-semibold">Add Subject</button>
                </div>
                <div id="subjectsList" class="space-y-4 mb-6"></div>
                <div class="bg-indigo-50 p-6 rounded-lg">
                    <div class="flex justify-between items-center">
                        <h3 class="text-xl font-bold text-indigo-800">GPA</h3>
                        <span id="gpaResult" class="text-3xl font-bold text-indigo-600">0.00</span>
                    </div>
                    <div class="text-sm text-gray-600 mt-2">Total Credits: <span id="totalCredits">0</span></div>
                </div>
            </div>
        </div>

        <!-- CGPA Calculator Section -->
        <div id="cgpaSection" class="max-w-4xl mx-auto hidden">
            <div class="bg-white/95 backdrop-blur-sm rounded-3xl shadow-2xl p-8 mb-8 border border-white/20 hover:shadow-3xl transition-all duration-500 transform hover:-translate-y-1">
                <div class="flex items-center mb-8">
                    <div class="w-1 h-8 bg-gradient-to-b from-indigo-500 to-purple-500 rounded-full mr-4"></div>
                    <h2 class="text-3xl font-bold bg-gradient-to-r from-indigo-600 to-purple-600 bg-clip-text text-transparent">CGPA Calculator</h2>
                </div>
                <div class="mb-6">
                    <button onclick="addSemester()" class="bg-gradient-to-r from-indigo-600 to-purple-600 text-white px-6 py-3 rounded-xl hover:from-indigo-700 hover:to-purple-700 transition-all duration-300 transform hover:scale-105 shadow-lg hover:shadow-xl font-semibold">Add Semester</button>
                </div>
                <div id="semestersList" class="space-y-4 mb-6"></div>
                <div class="bg-indigo-50 p-6 rounded-lg">
                    <div class="flex justify-between items-center">
                        <h3 class="text-xl font-bold text-indigo-800">CGPA</h3>
                        <span id="cgpaResult" class="text-3xl font-bold text-indigo-600">0.00</span>
                    </div>
                    <div class="text-sm text-gray-600 mt-2">Total Credits: <span id="totalCgpaCredits">0</span></div>
                </div>
            </div>
        </div>
    </div>

<script>
    // Tab switching functionality
    function showTab(tabName) {
        const sections = ['theorySection', 'labSection', 'theoryCumPracticalSection', 'gpaSection', 'cgpaSection'];
        const tabs = ['theoryTab', 'labTab', 'theoryCumPracticalTab', 'gpaTab', 'cgpaTab'];
        
        sections.forEach(sec => document.getElementById(sec).classList.add('hidden'));
        tabs.forEach(tab => {
            const btn = document.getElementById(tab);
            btn.className = 'px-6 py-3 rounded-xl text-indigo-600 hover:bg-indigo-50 font-semibold transition-all duration-300 transform hover:scale-105 whitespace-nowrap';
        });
        
        document.getElementById(tabName + 'Section').classList.remove('hidden');
        const activeButton = document.getElementById(tabName + 'Tab');
        activeButton.className = 'px-6 py-3 rounded-xl bg-indigo-600 text-white font-semibold transition-all duration-300 transform hover:scale-105 shadow-lg whitespace-nowrap';
    }

    // Theory calculation logic
    function calculateFAT() {
        const fat1Test = parseFloat(document.getElementById('fat1Test').value) || 0;
        const fat1Asg = parseFloat(document.getElementById('fat1Asg').value) || 0;
        const fat2Test = parseFloat(document.getElementById('fat2Test').value) || 0;
        const fat2Asg = parseFloat(document.getElementById('fat2Asg').value) || 0;
        const fat3Test = parseFloat(document.getElementById('fat3Test').value) || 0;
        const fat3Asg = parseFloat(document.getElementById('fat3Asg').value) || 0;
        const endSemScore = parseFloat(document.getElementById('endSemScore').value) || 0;

        const fat1Score = (fat1Test * 0.7) + (fat1Asg * 0.3);
        const fat2Score = (fat2Test * 0.7) + (fat2Asg * 0.3);
        const fat3Score = (fat3Test * 0.7) + (fat3Asg * 0.3);

        document.getElementById('fat1Result').textContent = fat1Score.toFixed(1);
        document.getElementById('fat2Result').textContent = fat2Score.toFixed(1);
        document.getElementById('fat3Result').textContent = fat3Score.toFixed(1);

        const internalAvg = ((fat1Score + fat2Score + fat3Score) / 3) * 0.8;
        const endSemMark = endSemScore * 0.6;
        const finalMark = internalAvg + endSemMark;

        document.getElementById('internalAvgResult').textContent = internalAvg.toFixed(1);
        document.getElementById('endSemResult').textContent = endSemMark.toFixed(1);
        document.getElementById('finalTheoryMark').textContent = finalMark.toFixed(1);

        const passFailElement = document.getElementById('theoryPassFail');
        if (finalMark >= 50 && endSemScore >= 45) {
            passFailElement.textContent = 'PASS';
            passFailElement.className = 'px-4 py-2 rounded-full text-sm font-bold bg-green-100 text-green-800';
        } else {
            passFailElement.textContent = 'FAIL';
            passFailElement.className = 'px-4 py-2 rounded-full text-sm font-bold bg-red-100 text-red-800';
        }
    }

    // Lab calculation logic
    function calculateLab() {
        const cat1Score = parseFloat(document.getElementById('cat1Score').value) || 0;
        const cat2Score = parseFloat(document.getElementById('cat2Score').value) || 0;
        const cat3Score = parseFloat(document.getElementById('cat3Score').value) || 0;
        const modelExamScore = parseFloat(document.getElementById('modelExamScore').value) || 0;
        const endSemesterScore = parseFloat(document.getElementById('endSemesterScore').value) || 0;

        document.getElementById('cat1Result').textContent = cat1Score.toFixed(1);
        document.getElementById('cat2Result').textContent = cat2Score.toFixed(1);
        document.getElementById('cat3Result').textContent = cat3Score.toFixed(1);
        document.getElementById('modelExamResult').textContent = modelExamScore.toFixed(1);
        document.getElementById('endSemesterResult').textContent = endSemesterScore.toFixed(1);

        const catAverage = (cat1Score + cat2Score + cat3Score) / 3;
        const internalMark = (catAverage * 0.8) + (modelExamScore * 0.2);
        const endSemesterMark = endSemesterScore * 0.4;
        const finalLabMark = internalMark + endSemesterMark;

        document.getElementById('internalMark').textContent = internalMark.toFixed(1);
        document.getElementById('finalLabMark').textContent = finalLabMark.toFixed(1);

        const labPassFailElement = document.getElementById('labPassFail');
        if (finalLabMark >= 50 && endSemesterScore >= 45) {
            labPassFailElement.textContent = 'PASS';
            labPassFailElement.className = 'px-4 py-2 rounded-full text-sm font-bold bg-green-100 text-green-800';
        } else {
            labPassFailElement.textContent = 'FAIL';
            labPassFailElement.className = 'px-4 py-2 rounded-full text-sm font-bold bg-red-100 text-red-800';
        }
    }

    // Theory cum Practical calculation
    function calculateTCP() {
        const cat1Score = parseFloat(document.getElementById('tcpCat1Score').value) || 0;
        const cat2Score = parseFloat(document.getElementById('tcpCat2Score').value) || 0;
        const modelScore = parseFloat(document.getElementById('tcpModelScore').value) || 0;
        const assignment1Score = parseFloat(document.getElementById('tcpAssignment1Score').value) || 0;
        const assignment2Score = parseFloat(document.getElementById('tcpAssignment2Score').value) || 0;
        const assignment3Score = parseFloat(document.getElementById('tcpAssignment3Score').value) || 0;
        const practicalScore = parseFloat(document.getElementById('tcpPracticalScore').value) || 0;
        const theoryScore = parseFloat(document.getElementById('tcpTheoryScore').value) || 0;

        const catAverage = (cat1Score + cat2Score + modelScore) / 3;
        const catPercentage = (catAverage / 50) * 70;
        const assignmentAverage = (assignment1Score + assignment2Score + assignment3Score) / 3;
        const assignmentPercentage = (assignmentAverage / 50) * 30;
        const combinedPercentage = catPercentage + assignmentPercentage;
        const totalInternal = combinedPercentage / 2;

        const practicalScaled = (practicalScore / 40) * 40;
        const theoryScaled = (theoryScore / 60) * 60;
        const totalExternal100 = practicalScaled + theoryScaled;
        const externalScaled50 = totalExternal100 / 2;

        const finalMark = totalInternal + externalScaled50;

        document.getElementById('tcpTotalInternal').textContent = totalInternal.toFixed(1);
        document.getElementById('tcpFinalMark').textContent = finalMark.toFixed(1);

        const tcpPassFailElement = document.getElementById('tcpPassFail');
        if (finalMark >= 50 && totalExternal100 >= 45) {
            tcpPassFailElement.textContent = 'PASS';
            tcpPassFailElement.className = 'px-4 py-2 rounded-full text-sm font-bold bg-green-100 text-green-800';
        } else {
            tcpPassFailElement.textContent = 'FAIL';
            tcpPassFailElement.className = 'px-4 py-2 rounded-full text-sm font-bold bg-red-100 text-red-800';
        }
    }

    // SGPA Calculator logic
    let subjectCount = 0;
    function addSubject() {
        subjectCount++;
        const subjectsList = document.getElementById('subjectsList');
        const subjectDiv = document.createElement('div');
        subjectDiv.className = 'bg-gray-50 p-4 rounded-lg';
        subjectDiv.id = `subject-${subjectCount}`;
        subjectDiv.innerHTML = `
            <div class="flex items-center justify-between mb-3">
                <h4 class="font-semibold text-gray-700">Subject ${subjectCount}</h4>
                <button onclick="removeSubject(${subjectCount})" class="text-red-500 hover:text-red-700" aria-label="Remove subject">
                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
                    </svg>
                </button>
            </div>
            <div class="grid grid-cols-2 gap-4">
                <div>
                    <label class="block text-sm font-medium text-gray-600 mb-1" for="grade-${subjectCount}">Grade</label>
                    <select id="grade-${subjectCount}" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" onchange="calculateGPA()">
                        <option value="">Select Grade</option>
                        <option value="0">U</option>
                        <option value="5">C</option>
                        <option value="6">B</option>
                        <option value="7">B+</option>
                        <option value="8">A</option>
                        <option value="9">A+</option>
                        <option value="10">O</option>
                    </select>
                </div>
                <div>
                    <label class="block text-sm font-medium text-gray-600 mb-1" for="credits-${subjectCount}">Credits</label>
                    <input type="number" id="credits-${subjectCount}" min="1" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Credits" oninput="calculateGPA()"/>
                </div>
            </div>
        `;
        subjectsList.appendChild(subjectDiv);
    }
    function removeSubject(id) {
        const subject = document.getElementById(`subject-${id}`);
        if (subject) {
            subject.remove();
            calculateGPA();
        }
    }
    function calculateGPA() {
        let totalGradePoints = 0;
        let totalCredits = 0;
        for (let i = 1; i <= subjectCount; i++) {
            const gradeInput = document.getElementById(`grade-${i}`);
            const creditsInput = document.getElementById(`credits-${i}`);
            if (gradeInput && creditsInput) {
                const gradePoints = parseFloat(gradeInput.value) || 0;
                const credits = parseFloat(creditsInput.value) || 0;
                if (gradePoints > 0 && credits > 0) {
                    totalGradePoints += gradePoints * credits;
                    totalCredits += credits;
                }
            }
        }
        const gpa = totalCredits > 0 ? totalGradePoints / totalCredits : 0;
        document.getElementById('gpaResult').textContent = gpa.toFixed(2);
        document.getElementById('totalCredits').textContent = totalCredits;
    }

    // CGPA Calculator logic
    let semesterCount = 0;
    function addSemester() {
        semesterCount++;
        const semestersList = document.getElementById('semestersList');
        const semesterDiv = document.createElement('div');
        semesterDiv.className = 'bg-gray-50 p-4 rounded-lg';
        semesterDiv.id = `semester-${semesterCount}`;
        semesterDiv.innerHTML = `
            <div class="flex items-center justify-between mb-3">
                <h4 class="font-semibold text-gray-700">Semester ${semesterCount}</h4>
                <button onclick="removeSemester(${semesterCount})" class="text-red-500 hover:text-red-700" aria-label="Remove semester">
                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
                    </svg>
                </button>
            </div>
            <div class="grid grid-cols-2 gap-4">
                <div>
                    <label class="block text-sm font-medium text-gray-600 mb-1" for="sgpa-${semesterCount}">GPA</label>
                    <input type="number" id="sgpa-${semesterCount}" max="10" min="0" step="0.01" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="0-10" oninput="calculateCGPA()"/>
                </div>
                <div>
                    <label class="block text-sm font-medium text-gray-600 mb-1" for="sem-credits-${semesterCount}">Credits</label>
                    <input type="number" id="sem-credits-${semesterCount}" min="1" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Credits" oninput="calculateCGPA()"/>
                </div>
            </div>
        `;
        semestersList.appendChild(semesterDiv);
    }
    function removeSemester(id) {
        const semester = document.getElementById(`semester-${id}`);
        if (semester) {
            semester.remove();
            calculateCGPA();
        }
    }
    function calculateCGPA() {
        let totalGradePoints = 0;
        let totalCredits = 0;
        for (let i = 1; i <= semesterCount; i++) {
            const sgpaInput = document.getElementById(`sgpa-${i}`);
            const creditsInput = document.getElementById(`sem-credits-${i}`);
            if (sgpaInput && creditsInput) {
                const gpa = parseFloat(sgpaInput.value) || 0;
                const credits = parseFloat(creditsInput.value) || 0;
                totalGradePoints += gpa * credits;
                totalCredits += credits;
            }
        }
        const cgpa = totalCredits > 0 ? totalGradePoints / totalCredits : 0;
        document.getElementById('cgpaResult').textContent = cgpa.toFixed(2);
        document.getElementById('totalCgpaCredits').textContent = totalCredits;
    }

    document.addEventListener('DOMContentLoaded', function() {
        addSubject();
        addSemester();
        showTab('theory'); // default tab
    });
</script>
</body>
</html>
