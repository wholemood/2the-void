<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MILEHIGH.WORLD: INTO THE VOID - Grant Proposal</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/marked/marked.min.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Warm Neutral Harmony -->
    <!-- Application Structure Plan: The SPA is designed as a sequential, scrollable grant proposal, with each section representing a key part of a grant application. A sticky top navigation bar allows direct jumping to any major section. Within the financial section, a sub-navigation bar provides quick access to detailed cost breakdowns and funding strategies. Interactive charts (bar, donut) and HTML/CSS diagrams (flowchart) are used to visualize key data and concepts, making complex information digestible. -->
    <!-- Visualization & Content Choices: Project Summary: Goal: Inform, Hook. Viz: Large text, hero image concept. Justification: Sets immediate tone and provides concise overview. Project Narrative: Goal: Inform, Explain. Viz: Headline, bullet points, HTML/CSS flow diagram. Justification: Details project mechanics and innovations. Ask Omega.one: Goal: Interact, Demonstrate AI. Viz: Text input, button, LLM response. Justification: Directly showcases Gemini API integration and in-game AI. Financials: Goal: Inform, Justify. Viz: Interactive dashboard with bar/donut charts, AI insights. Justification: Provides detailed budget, cost drivers, and AI-powered financial analysis. Funding & Allocation: Goal: Inform, Justify. Viz: Donut chart for fund use, roadmap. Justification: Presents funding request and project timeline. Grant Potential: Goal: Inform, Strategize. Viz: Textual analysis with bullet points. Justification: Outlines alignment with grant priorities and strategic recommendations. Public Benefit: Goal: Inform, Impact. Viz: Bar Chart (Chart.js/Canvas). Justification: Visualizes societal impact alignment. Organizational Capacity: Goal: Inform, Credibility. Viz: Textual personnel info. Justification: Builds team trust. Contact: Goal: Call to Action. Viz: Text, contact info. Justification: Clear closing. -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #FDFBF8; /* Light background from warm neutral palette */
            color: #333333; /* Dark text for readability */
        }
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 1.5rem; /* Increased padding */
        }
        .section-padding {
            padding: 5rem 1.5rem; /* Increased padding */
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
        }
        @media (min-width: 768px) {
            .section-padding {
                padding: 7rem 2rem; /* Increased padding */
            }
        }
        .card {
            background-color: #FFFFFF;
            border-radius: 0.75rem;
            box-shadow: 0 6px 16px rgba(0, 0, 0, 0.1); /* Stronger shadow for elevation */
            padding: 2rem; /* Increased padding */
            border: 1px solid #E0E0E0;
        }
        .accent-color-primary {
            color: #4A5568;
        }
        .accent-color-secondary {
            color: #6B46C1;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 550px;
            margin-left: auto;
            margin-right: auto;
            height: 320px;
            max-height: 450px;
        }
        @media (min-width: 768px) {
            .chart-container {
                height: 380px;
            }
        }
        .flow-box {
            background-color: #F0F0F0;
            padding: 1.25rem 1.75rem; /* Increased padding */
            border-radius: 0.5rem;
            font-weight: 600;
            color: #4A5568;
            flex-shrink: 0;
            min-width: 180px; /* Slightly wider */
        }
        .flow-arrow {
            font-size: 3rem; /* Larger arrow */
            color: #A0AEC0;
            margin: 0 1.5rem; /* Increased margin */
        }
        .bg-grid {
            background-image: linear-gradient(to right, #f0f0f0 1px, transparent 1px), linear-gradient(to bottom, #f0f0f0 1px, transparent 1px);
            background-size: 20px 20px;
        }

        /* Styles from the new cost analysis file */
        .stat-card {
            background-color: white;
            border-radius: 0.75rem;
            padding: 1.5rem;
            box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .stat-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
        }
        .toggle-bg:after {
            content: '';
            position: absolute;
            top: 2px;
            left: 2px;
            width: 20px;
            height: 20px;
            background-color: white;
            border-radius: 9999px;
            transition: transform 0.3s ease-in-out;
        }
        input:checked + .toggle-bg:after {
            transform: translateX(100%);
            transform: translateX(20px);
        }
        .gemini-output h3 {
            font-size: 1.25rem; /* text-xl */
            font-weight: 700;
            margin-top: 2rem; /* mt-8 */
            margin-bottom: 0.75rem; /* mb-3 */
            color: #1e293b;
        }
        .gemini-output ul {
            list-style-position: inside;
            list-style-type: disc;
            padding-left: 1.5rem; /* pl-6 */
            margin-bottom: 1.25rem; /* mb-5 */
        }
        .gemini-output li {
            margin-bottom: 0.6rem; /* mb-2.5 */
        }
        .gemini-output p {
            margin-bottom: 1.25rem; /* mb-5 */
        }
        /* Specific chart container heights for cost analysis charts */
        #financial-personnel .chart-container { height: 600px; max-height: 800px; }
        #financial-operations .chart-container { height: 500px; max-height: 500px; }
        #financial-development .chart-container { height: 350px; max-height: 400px; }
        @media (min-width: 768px) {
            #financial-personnel .chart-container { height: 800px; }
            #financial-development .chart-container { height: 400px; }
        }

        /* Hero image styling */
        .hero-section {
            background-image: url('https://placehold.co/1920x1080/4A5568/FFFFFF?text=MILEHIGH.WORLD+Hero'); /* Placeholder for hero image */
            background-size: cover;
            background-position: center;
            color: white;
            text-shadow: 0 2px 4px rgba(0,0,0,0.5);
            position: relative;
            z-index: 0;
        }
        .hero-section::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0,0,0,0.4); /* Slightly darker overlay for text readability */
            z-index: -1;
        }

        /* Styling for the new grant analysis section */
        #grant-potential h2 {
            font-size: 2.5rem; /* text-4xl */
            font-weight: 700; /* font-bold */
            color: #4A5568; /* accent-color-primary */
            margin-bottom: 2rem; /* mb-8 */
        }
        #grant-potential h3 {
            font-size: 1.75rem; /* text-3xl */
            font-weight: 600; /* font-semibold */
            color: #4A5568; /* accent-color-primary */
            margin-top: 2.5rem; /* mt-10 */
            margin-bottom: 1rem; /* mb-4 */
        }
        #grant-potential p, #grant-potential li {
            color: #4A5568; /* text-gray-700 / text-gray-600 */
            line-height: 1.7; /* Improved line height */
            margin-bottom: 1rem;
        }
        #grant-potential ul {
            list-style-type: disc;
            list-style-position: outside; /* Outside for better alignment */
            padding-left: 1.5rem; /* pl-6 */
        }
        #grant-potential strong {
            font-weight: 600;
            color: #333333;
        }

        /* Sub-navigation for financial overview */
        .sub-nav {
            background-color: #FDFBF8; /* Light background */
            border-bottom: 1px solid #E0E0E0;
            padding: 0.75rem 0;
            position: sticky;
            top: 4rem; /* Below main nav */
            z-index: 40;
            box-shadow: 0 2px 4px rgba(0,0,0,0.05);
        }
        .sub-nav a {
            padding: 0.5rem 1rem;
            border-radius: 0.375rem;
            font-weight: 500;
            color: #6B46C1; /* Accent secondary */
            transition: background-color 0.2s ease, color 0.2s ease;
        }
        .sub-nav a:hover {
            background-color: #EDE9FE; /* Light indigo hover */
            color: #553C9A; /* Darker indigo */
        }
    </style>
</head>
<body>

    <header class="bg-white/90 backdrop-blur-sm sticky top-0 z-50 shadow-md">
        <nav class="container mx-auto px-6 py-3">
            <div class="flex items-center justify-between">
                <div class="text-xl font-bold text-gray-800">MILEHIGH.WORLD</div>
                <div class="hidden md:flex items-center space-x-6">
                    <a href="#project-summary" class="text-gray-600 hover:text-indigo-600 transition-colors duration-200">Summary</a>
                    <a href="#project-narrative" class="text-gray-600 hover:text-indigo-600 transition-colors duration-200">Narrative</a>
                    <a href="#budget-financials" class="text-gray-600 hover:text-indigo-600 transition-colors duration-200">Financials</a>
                    <a href="#public-benefit" class="text-gray-600 hover:text-indigo-600 transition-colors duration-200">Impact</a>
                    <a href="#organizational-capacity" class="text-gray-600 hover:text-indigo-600 transition-colors duration-200">Team</a>
                    <a href="#contact-info" class="text-gray-600 hover:text-indigo-600 transition-colors duration-200">Contact</a>
                </div>
                <div class="md:hidden">
                    <button id="mobile-menu-btn" class="text-gray-600 focus:outline-none">
                        <span class="block w-6 h-0.5 bg-gray-600"></span>
                        <span class="block w-6 h-0.5 bg-gray-600 mt-1.5"></span>
                        <span class="block w-6 h-0.5 bg-gray-600 mt-1.5"></span>
                    </button>
                </div>
            </div>
            <div id="mobile-menu" class="hidden md:hidden mt-4">
                <a href="#project-summary" class="block py-2 px-4 text-sm text-gray-600 hover:bg-gray-100 rounded">Summary</a>
                <a href="#project-narrative" class="block py-2 px-4 text-sm text-gray-600 hover:bg-gray-100 rounded">Narrative</a>
                <a href="#budget-financials" class="block py-2 px-4 text-sm text-gray-600 hover:bg-gray-100 rounded">Financials</a>
                <a href="#public-benefit" class="block py-2 px-4 text-sm text-gray-600 hover:bg-gray-100 rounded">Impact</a>
                <a href="#organizational-capacity" class="block py-2 px-4 text-sm text-gray-600 hover:bg-gray-100 rounded">Team</a>
                <a href="#contact-info" class="block py-2 px-4 text-sm text-gray-600 hover:bg-gray-100 rounded">Contact</a>
            </div>
        </nav>
    </header>

    <main>
        <!-- Section 1: Project Summary (Executive Summary / Introduction / Statement of Need) -->
        <section id="project-summary" class="section-padding hero-section">
            <h1 class="text-5xl md:text-7xl font-extrabold text-white leading-tight">MILEHIGH.WORLD: <span class="text-red-400">INTO THE VOID</span></h1>
            <p class="mt-4 max-w-3xl mx-auto text-lg md:text-xl text-white">A New Horizon for Interactive Storytelling and Human Connection</p>
            <p class="mt-8 text-sm text-gray-200">MILEHIGH-WORLD LLC</p>

            <div class="mt-16 card max-w-4xl mx-auto bg-white/90 backdrop-blur-sm p-8 text-gray-800">
                <h2 class="text-3xl font-bold accent-color-primary mb-4">Executive Summary</h2>
                <p class="text-lg mb-4">
                    "MILEHIGH.WORLD: INTO THE VOID" is an immersive, narrative-driven virtual reality (VR) experience that uniquely combines a single-player role-playing game (RPG) with a massively multiplayer online (MMO) world. Set in a rich science-fantasy universe, the project uses cutting-edge technology, including generative AI, to explore profound themes of human connection, resilience, and ethical decision-making. Our primary goal is to create a platform that not only entertains but also offers significant public value in the arts, humanities, education, and mental well-being.
                </p>
                <h3 class="text-xl font-semibold accent-color-primary mb-3">Statement of Need</h3>
                <p class="text-base text-gray-700">
                    In the rapidly growing VR market, there is a noticeable gap in experiences that offer both deep, personal narratives and large-scale, collaborative gameplay. Existing titles often focus on either isolated single-player stories or competitive multiplayer action, leaving a space for a project that fosters both individual reflection and community building. Furthermore, there's a significant opportunity to leverage the immersive power of VR for more than just entertainment. "MILEHIGH.WORLD" addresses this by creating an interactive world that promotes critical thinking, empathy, and positive psychological development, aligning with the missions of national endowments and foundations dedicated to public good.
                </p>
            </div>
        </section>

        <!-- Section 2: Project Narrative & Methodology -->
        <section id="project-narrative" class="section-padding bg-white">
            <h2 class="text-4xl md:text-5xl font-bold accent-color-primary mb-8">Project Narrative & Methodology</h2>
            <p class="max-w-4xl mx-auto text-lg text-gray-700 mb-12">
                This section details the core concept, gameplay mechanics, technological innovations, and the strategic plan for bringing "MILEHIGH.WORLD: INTO THE VOID" to fruition.
            </p>

            <div class="card w-full max-w-5xl mb-12">
                <h3 class="text-2xl font-semibold accent-color-primary mb-6">Core Gameplay & Dual-Phase Journey</h3>
                <p class="text-lg text-gray-700 mb-8">
                    The game is set in the fractured multiverse of Mîlēhigh.wørld, where players become "Növəmînād"—heroes prophesied to confront a digital abyss known as The Void. Each of the ten playable characters has a unique storyline and a special ability called a "Channah Manifest," a power that grows with their moral and emotional development.
                </p>
                <div class="flex flex-col md:flex-row items-center justify-center w-full max-w-5xl mx-auto">
                    <div class="flow-box">
                        <h4 class="text-lg font-bold mb-2">Phase 1: The Character Saga</h4>
                        <ul class="list-none p-0 m-0 text-sm text-left space-y-1">
                            <li>Deep, character-driven story.</li>
                            <li>Master unique abilities: <strong class="text-indigo-700">Channah Manifests</strong>.</li>
                            <li>Forge your identity and purpose.</li>
                        </ul>
                    </div>
                    <span class="flow-arrow md:rotate-0 rotate-90">→</span>
                    <div class="flow-box">
                        <h4 class="text-lg font-bold mb-2">Phase 2: The MMO Universe</h4>
                        <ul class="list-none p-0 m-0 text-sm text-left space-y-1">
                            <li>Join a persistent, evolving world.</li>
                            <li>Form 'Fates' for cooperative challenges.</li>
                            <li>Unleash powerful <strong class="text-indigo-700">Alliance Powers</strong> with your team.</li>
                        </ul>
                    </div>
                </div>
                <p class="mt-8 max-w-3xl mx-auto text-lg text-gray-700">
                    This dual-loop design bridges the gap between in-depth storytelling and massive multiplayer action, creating a sustainable and replayable experience.
                </p>
            </div>

            <div class="card w-full max-w-5xl mb-12">
                <h3 class="text-2xl font-semibold accent-color-primary mb-6">World Setting & Lore: Mîlēhigh.wørld</h3>
                <p class="max-w-4xl mx-auto text-lg text-gray-700 mb-8">
                    Explore a fractured multiverse where advanced technology coexists with ancient spirituality. As a Növəmînād, you are one of ten prophesied heroes destined to save reality from The Void, a corrupting digital abyss.
                </p>
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 w-full max-w-5xl mb-8">
                    <!-- Image with onerror fallback -->
                    <img src="image.png-85e98d72-108a-45e8-a9bb-6e8fe159270a.jpeg" alt="Character with winged lion in white city" class="w-full h-48 object-cover rounded-lg shadow-md" onerror="this.onerror=null;this.src='https://placehold.co/400x200/A0AEC0/FFFFFF?text=Image+Unavailable';">
                    <img src="image.png-492e7462-99a7-458e-95ca-412f2927438a.jpeg" alt="Character with bow in white city" class="w-full h-48 object-cover rounded-lg shadow-md" onerror="this.onerror=null;this.src='https://placehold.co/400x200/A0AEC0/FFFFFF?text=Image+Unavailable';">
                    <img src="image.png-5d6e1a59-f2fd-49c0-bf96-32dde02efa9a.jpeg" alt="Character and winged lion looking at city" class="w-full h-48 object-cover rounded-lg shadow-md" onerror="this.onerror=null;this.src='https://placehold.co/400x200/A0AEC0/FFFFFF?text=Image+Unavailable';">
                    <img src="image.png-1d794e79-4749-4a6d-8bda-deb3129ef0bf.jpeg" alt="Two characters with wings and lion, volcanic background" class="w-full h-48 object-cover rounded-lg shadow-md" onerror="this.onerror=null;this.src='https://placehold.co/400x200/A0AEC0/FFFFFF?text=Image+Unavailable';">
                    <img src="image.png-92d04793-e8bb-43cd-b810-26448073542e.jpeg" alt="Character with fire magic" class="w-full h-48 object-cover rounded-lg shadow-md" onerror="this.onerror=null;this.src='https://placehold.co/400x200/A0AEC0/FFFFFF?text=Image+Unavailable';">
                    <img src="image.png-cb3b0971-407f-4daa-901d-83a8f5dd9cc8.jpeg" alt="Character with two swords" class="w-full h-48 object-cover rounded-lg shadow-md" onerror="this.onerror=null;this.src='https://placehold.co/400x200/A0AEC0/FFFFFF?text=Image+Unavailable';">
                </div>
                <div class="grid md:grid-cols-2 gap-8 w-full max-w-5xl">
                    <div class="card p-6">
                        <h4 class="text-xl font-semibold accent-color-primary mb-2">The Void</h4>
                        <p class="text-gray-600">A sentient force of chaos and decay, threatening to consume all existence.</p>
                    </div>
                    <div class="card p-6">
                        <h4 class="text-xl font-semibold accent-color-primary mb-2">Channah Manifests</h4>
                        <p class="text-gray-600">Mystical powers unlocked through personal growth, inner conviction, and grace.</p>
                    </div>
                    <div class="card p-6 md:col-span-2">
                        <h4 class="text-xl font-semibold accent-color-primary mb-2">The Lost Prophecy</h4>
                        <p class="text-gray-600">A guide to uniting the Növəmînād and achieving "Millenia," an era of enduring peace.</p>
                    </div>
                </div>
            </div>

            <div class="card w-full max-w-5xl mb-12">
                <h3 class="text-2xl font-semibold accent-color-primary mb-6">Technological Innovation & Implementation</h3>
                <p class="text-lg text-gray-700 mb-8">
                    "MILEHIGH.WORLD: INTO THE VOID" leverages cutting-edge technology to create an unparalleled immersive experience.
                </p>
                <div class="grid md:grid-cols-3 gap-8 w-full">
                    <div class="card flex flex-col items-center p-6">
                        <span class="text-5xl mb-4">🤖</span>
                        <h4 class="text-xl font-semibold accent-color-primary mb-2">Advanced AI Companion (Omega.one)</h4>
                        <p class="text-gray-600">Powered by Google's Gemini, Omega.one offers players dynamic, context-aware dialogue and strategic advice, evolving with their journey.</p>
                    </div>
                    <div class="card flex flex-col items-center p-6">
                        <span class="text-5xl mb-4">🚀</span>
                        <h4 class="text-xl font-semibold accent-color-primary mb-2">High-Performance Standalone VR</h4>
                        <p class="text-gray-600">Optimized for a seamless 90 FPS on Meta Quest 3, ensuring an accessible, high-quality experience without requiring expensive PC hardware.</p>
                    </div>
                    <div class="card flex flex-col items-center p-6">
                        <span class="text-5xl mb-4">🌐</span>
                        <h4 class="text-xl font-semibold accent-color-primary mb-2">Scalable MMO Architecture</h4>
                        <p class="text-gray-600">A custom, cloud-based server infrastructure using Firebase/Firestore to support a persistent, shared world for thousands of simultaneous players.</p>
                    </div>
                </div>

                <div class="mt-12">
                    <h3 class="text-2xl font-semibold accent-color-primary mb-6">Demonstration of Core Technology: Ask Omega.one ✨</h3>
                    <p class="max-w-3xl mx-auto text-lg text-gray-700 mb-8">
                        Experience a glimpse of Omega.one's capabilities. Ask your in-game AI companion, anything about the project, its lore, or its impact.
                    </p>
                    <div class="card w-full max-w-2xl p-6 mx-auto">
                        <textarea id="omega-input" class="w-full p-3 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500 mb-4 text-gray-700" rows="4" placeholder="e.g., What is The Void?"></textarea>
                        <button id="ask-omega-btn" class="bg-indigo-600 text-white px-6 py-3 rounded-md hover:bg-indigo-700 transition-colors duration-200 font-semibold text-lg shadow-md">
                            Ask Omega.one ✨
                        </button>
                        <div id="omega-response" class="mt-6 p-4 bg-gray-100 rounded-md text-gray-800 text-left min-h-[100px] flex items-center justify-center">
                            <p class="text-gray-500">Omega.one awaits your query...</p>
                        </div>
                        <div id="omega-loading" class="hidden mt-4 text-indigo-600 font-medium">Loading...</div>
                    </div>
                </div>
            </div>

            <div class="card w-full max-w-5xl">
                <h3 class="text-2xl font-semibold accent-color-primary mb-6">Goals & Objectives</h3>
                <p class="text-lg text-gray-700 mb-8">
                    Our project goals are designed to achieve specific, measurable outcomes that align with both our mission and the public good.
                </p>
                <div class="grid md:grid-cols-2 gap-8 w-full">
                    <div class="p-6 text-left">
                        <h4 class="text-xl font-bold accent-color-primary mb-2">Goal 1: Advance Interactive Storytelling.</h4>
                        <ul class="list-disc pl-5 space-y-1 text-gray-600">
                            <li>**Objective:** Develop and launch a VR game with a compelling, branching narrative that integrates player choice and moral consequence.</li>
                        </ul>
                    </div>
                    <div class="p-6 text-left">
                        <h4 class="text-xl font-bold accent-color-primary mb-2">Goal 2: Foster Pro-Social Behavior and Resilience.</h4>
                        <ul class="list-disc pl-5 space-y-1 text-gray-600">
                            <li>**Objective:** Implement gameplay mechanics (Channah Manifests, Alliance Powers) that reward cooperation and perseverance.</li>
                            <li>**Objective:** Partner with a research institution to measure the game's impact on players' empathy and problem-solving skills.</li>
                        </ul>
                    </div>
                    <div class="p-6 text-left md:col-span-2">
                        <h4 class="text-xl font-bold accent-color-primary mb-2">Goal 3: Innovate in VR and AI Technology.</h4>
                        <ul class="list-disc pl-5 space-y-1 text-gray-600">
                            <li>**Objective:** Successfully deploy a persistent MMO on a standalone VR platform.</li>
                            <li>**Objective:** Demonstrate the effective use of a large language model (LLM) for a dynamic in-game character.</li>
                        </ul>
                    </div>
                </div>
            </div>
        </section>

        <!-- Section 3: Budget & Financials -->
        <section id="budget-financials" class="py-16 md:py-20 text-slate-800 bg-slate-50">
            <div class="container mx-auto px-6">
                <h1 class="text-3xl md:text-5xl font-extrabold text-slate-900 mb-8">Budget & Financials</h1>
                <p class="mt-4 max-w-3xl mx-auto text-lg text-slate-600 mb-12">
                    A detailed breakdown of "MILEHIGH.WORLD: INTO THE VOID"'s estimated development and operational costs, funding strategy, and grant potential.
                </p>
            </div>

            <!-- Financial Sub-Navigation -->
            <nav class="sub-nav w-full text-center">
                <div class="container mx-auto flex flex-wrap justify-center space-x-2 md:space-x-4">
                    <a href="#financial-overview-summary" class="hover:underline">Overview</a>
                    <a href="#financial-development" class="hover:underline">Development</a>
                    <a href="#financial-personnel" class="hover:underline">Personnel</a>
                    <a href="#financial-operations" class="hover:underline">Operations</a>
                    <a href="#financial-insights" class="hover:underline">AI Insights</a>
                    <a href="#financial-funding-grants" class="hover:underline">Funding & Grants</a>
                </div>
            </nav>

            <!-- Sub-section: Project Financial Overview Summary -->
            <div id="financial-overview-summary" class="py-16 md:py-20 bg-slate-50">
                <div class="container mx-auto px-6">
                    <h2 class="text-3xl md:text-4xl font-bold text-slate-900 mb-8">Project Financial Overview</h2>
                    <p class="mt-4 max-w-3xl mx-auto text-lg text-slate-600 mb-8">
                        An interactive dashboard analyzing the estimated development and operational costs for the AAA VR MMO, "MILEHIGH.WORLD: INTO THE VOID".
                    </p>
                    <div class="mt-8 flex justify-center items-center space-x-4">
                        <span id="toggle-label-low" class="font-semibold text-blue-600">Conservative Estimate</span>
                        <label for="budget-toggle" class="flex items-center cursor-pointer">
                            <div class="relative">
                                <input type="checkbox" id="budget-toggle" class="sr-only">
                                <div class="toggle-bg block bg-slate-300 w-11 h-6 rounded-full"></div>
                            </div>
                        </label>
                        <span id="toggle-label-high" class="font-semibold text-slate-400">Ambitious Estimate</span>
                    </div>

                    <div class="mt-12 grid grid-cols-1 md:grid-cols-3 gap-6 max-w-5xl mx-auto">
                        <div class="stat-card">
                            <h3 class="text-sm font-medium text-slate-500 uppercase">Total Development Budget</h3>
                            <p id="total-budget" class="text-4xl font-extrabold text-blue-600 mt-2">$50M</p>
                            <p class="text-xs text-slate-400 mt-1">Pre-production to Launch</p>
                        </div>
                        <div class="stat-card">
                            <h3 class="text-sm font-medium text-slate-500 uppercase">Est. Development Time</h3>
                            <p class="text-4xl font-extrabold text-slate-800 mt-2">3 - 4.5</p>
                            <p class="text-xs text-slate-400 mt-1">Years</p>
                        </div>
                        <div class="stat-card">
                            <h3 class="text-sm font-medium text-slate-500 uppercase">Est. Team Size</h3>
                            <p class="text-4xl font-extrabold text-slate-800 mt-2">140 - 280</p>
                            <p class="text-xs text-slate-400 mt-1">Full-Time Equivalents</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Sub-section: Development Cost Breakdown -->
            <div id="financial-development" class="py-16 md:py-20 bg-slate-100">
                <div class="container mx-auto px-6">
                    <div class="text-center mb-12">
                        <h2 class="text-3xl md:text-4xl font-bold text-slate-900">Development Cost Breakdown</h2>
                        <p class="mt-3 max-w-2xl mx-auto text-slate-600">This section visualizes how the total budget is allocated across different development phases and key cost categories. Interact with the toggle above to see how estimates change.</p>
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-5 gap-8 items-start">
                        <div class="lg:col-span-3 bg-white p-6 rounded-xl shadow-lg">
                            <h3 class="font-bold text-lg text-slate-800 mb-4">Cost Allocation by Development Phase</h3>
                            <div class="chart-container">
                                <canvas id="phaseChart"></canvas>
                            </div>
                        </div>
                        <div class="lg:col-span-2 bg-white p-6 rounded-xl shadow-lg">
                            <h3 class="font-bold text-lg text-slate-800 mb-4">Primary Cost Drivers</h3>
                            <div class="chart-container">
                                <canvas id="driverChart"></canvas>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Sub-section: Personnel Costs -->
            <div id="financial-personnel" class="py-16 md:py-20 bg-white">
                <div class="container mx-auto px-6">
                    <div class="text-center mb-12">
                        <h2 class="text-3xl md:text-4xl font-bold text-slate-900">Personnel: The Core Expense</h2>
                        <p class="mt-3 max-w-2xl mx-auto text-slate-600">Personnel is the largest single cost. This chart illustrates the estimated annual budget required for each development discipline, forming the bulk of the project's expense.</p>
                    </div>
                    <div class="bg-white p-6 rounded-xl shadow-lg max-w-6xl mx-auto">
                        <h3 class="font-bold text-lg text-slate-800 mb-4">Estimated Annual Cost by Discipline</h3>
                        <div class="chart-container">
                            <canvas id="personnelChart"></canvas>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Sub-section: Post-Launch Operational Overhead -->
            <div id="financial-operations" class="py-16 md:py-20 bg-slate-100">
                <div class="container mx-auto px-6">
                    <div class="text-center mb-12">
                        <h2 class="text-3xl md:text-4xl font-bold text-slate-900">Post-Launch Operational Overhead</h2>
                        <p class="mt-3 max-w-2xl mx-auto text-slate-600">A live-service MMO incurs significant ongoing costs. This visualization compares the estimated annual operational expenses based on low vs. high player engagement, highlighting the scalable nature of infrastructure like servers, databases, and AI services.</p>
                    </div>
                    <div class="bg-white p-6 rounded-xl shadow-lg max-w-5xl mx-auto">
                        <h3 class="font-bold text-lg text-slate-800 mb-4">Annual Operational Costs (Low vs. High Engagement)</h3>
                        <div class="chart-container">
                            <canvas id="opsChart"></canvas>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Sub-section: AI-Powered Strategic Insights -->
            <div id="financial-insights" class="py-16 md:py-20 bg-white">
                <div class="container mx-auto px-6">
                    <div class="text-center mb-12">
                        <h2 class="text-3xl md:text-4xl font-bold text-slate-900">✨ AI-Powered Strategic Insights</h2>
                        <p class="mt-3 max-w-2xl mx-auto text-slate-600">Leverage the power of Gemini to analyze the current budget scenario. Generate a high-level executive summary, identify key risks, and discover potential cost-saving opportunities.</p>
                        <button id="generate-insights-btn" class="mt-8 bg-blue-600 text-white font-bold py-3 px-6 rounded-lg hover:bg-blue-700 transition-colors shadow-md hover:shadow-lg">
                            Generate Executive Summary
                        </button>
                    </div>
                    <div id="insights-container" class="bg-white p-6 md:p-8 rounded-xl shadow-lg max-w-4xl mx-auto hidden">
                        <div id="insights-output" class="prose max-w-none gemini-output text-slate-600">
                            <!-- Gemini output will be rendered here -->
                        </div>
                        <div id="loading-indicator" class="text-center hidden">
                            <svg class="animate-spin h-8 w-8 text-blue-600 mx-auto" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
                                <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
                                <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
                            </svg>
                            <p class="mt-4 text-slate-500">Generating analysis... Please wait.</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Sub-section: Funding Request & Allocation and Grant Potential & Strategy -->
            <div id="financial-funding-grants" class="py-16 md:py-20 bg-slate-100">
                <div class="container mx-auto px-6">
                    <h2 class="text-3xl md:text-4xl font-bold accent-color-primary mb-12">Funding Request & Grant Strategy</h2>
                    <div class="grid lg:grid-cols-2 gap-8 w-full max-w-5xl items-center">
                        <div class="chart-container">
                            <canvas id="fundingChart"></canvas>
                        </div>
                        <div class="text-left">
                            <h3 class="text-2xl font-bold accent-color-primary mb-4">Funding Request: <span class="text-indigo-600">$75,000,000 USD</span></h3>
                            <p class="text-gray-700 mb-6">Funding is requested to support the 24-month development cycle, ensuring the successful delivery of a landmark VR MMO.</p>
                            <h4 class="text-xl font-semibold accent-color-primary mb-3">Roadmap:</h4>
                            <ul class="space-y-3 text-gray-600">
                                <li class="flex items-start">
                                    <span class="text-indigo-500 font-bold mr-3 mt-1">●</span>
                                    <div><strong>Phase 1 (Months 1-9):</strong> Pre-production & Vertical Slice - Finalize core mechanics, AI integration, and build a polished demo.</div>
                                </li>
                                <li class="flex items-start">
                                    <span class="text-indigo-500 font-bold mr-3 mt-1">●</span>
                                    <div><strong>Phase 2 (Months 10-18):</strong> Full Production - Develop all character campaigns, build MMO world zones, and conduct alpha testing.</div>
                                </li>
                                <li class="flex items-start">
                                    <span class="text-indigo-500 font-bold mr-3 mt-1">●</span>
                                    <div><strong>Phase 3 (Months 19-24):</strong> Beta, Polish, and Launch - Extensive testing, community feedback, marketing, and public release on Meta Quest Store.</div>
                                </li>
                            </ul>
                        </div>
                    </div>

                    <div class="card mt-16 p-8 text-left max-w-4xl mx-auto">
                        <h3 class="text-2xl font-semibold accent-color-primary mb-6">Grant Potential & Strategy</h3>
                        <p class="text-lg text-gray-700 mb-4">
                            "MILEHIGH.WORLD: INTO THE VOID" is positioned as a "serious game" or "applied game," aligning with federal grant opportunities that primarily target projects serving specific public interest objectives rather than purely commercial entertainment.
                        </p>

                        <h4 class="text-xl font-semibold accent-color-primary mt-8 mb-3">Key Alignments with Grant Priorities:</h4>
                        <ul class="list-disc pl-5 space-y-2 text-gray-600">
                            <li><strong class="text-gray-800">Public Benefit & Mission Alignment:</strong> Focus on resilience, collaboration, personal growth, and research in digital humanities, education, and psychological well-being.</li>
                            <li><strong class="text-gray-800">Technological Innovation:</strong> Leveraging next-generation AI (Gemini) and VR (Meta Quest 3 optimization) for novel solutions.</li>
                            <li><strong class="text-gray-800">Interdisciplinary Collaboration:</strong> Actively seeking partnerships with universities, non-profit organizations, and humanities researchers.</li>
                            <li><strong class="text-gray-800">Measurable Outcomes & Evaluation:</strong> Commitment to demonstrating impact through rigorous evaluation.</li>
                        </ul>

                        <h4 class="text-xl font-semibold accent-color-primary mt-8 mb-3">Expanded Platform Strategy:</h4>
                        <p class="text-lg text-gray-700 mb-4">
                            While initially targeting Meta Quest, "MILEHIGH.WORLD: INTO THE VOID" is designed with a multi-platform strategy to maximize reach and impact. Expanding to PC (via Steam) and Microsoft (Xbox) significantly broadens the potential player base, increases revenue streams, and enhances the project's long-term sustainability. This wider accessibility allows the game's public benefit themes to reach a much larger and more diverse audience, strengthening its appeal to funders looking for widespread societal impact.
                        </p>

                        <h4 class="text-xl font-semibold accent-color-primary mt-8 mb-3">Strategic Recommendations for Grant Pursuit:</h4>
                        <ul class="list-disc pl-5 space-y-2 text-gray-600">
                            <li><strong class="text-gray-800">Prioritize SBIR/STTR:</strong> For a for-profit entity, the SBIR/STTR programs offer the most direct federal funding pathway.</li>
                            <li><strong class="text-gray-800">Forge Strong Non-Profit/Academic Partnerships:</strong> For NEH, NEA, ED, and potentially some NIH grants, formalizing partnerships with eligible non-profit organizations is crucial.</li>
                            <li><strong class="text-gray-800">Develop Rigorous Evaluation Plans:</strong> For any grant application emphasizing public benefit, integrate a robust, measurable evaluation plan from the outset.</li>
                            <li><strong class="text-gray-800">Deep Dive into Specific FOAs/RFPs:</strong> Continuously monitor Grants.gov and relevant agency websites for specific Funding Opportunity Announcements.</li>
                            <li><strong class="text-gray-800">Emphasize Research and Scholarly Rigor:</strong> For NEH and NIH grants, demonstrate how the game incorporates "sound humanities scholarship" or "rigorous scientific methodology."</li>
                            <li><strong class="text-gray-800">Initiate Pre-Application Registrations Early:</strong> SAM.gov and Grants.gov registrations are mandatory and time-consuming.</li>
                            <li><strong class="text-gray-800">Leverage the Federal Games Guild:</strong> Engage with this community for insights into emerging needs and priorities across federal agencies.</li>
                            <li><strong class="text-gray-800">Refine Budget Narratives:</strong> Ensure the budget breakdown clearly links each cost item to the achievement of grant objectives and provides detailed justifications.</li>
                        </ul>
                    </div>
                </div>
            </div>
        </section>

        <!-- Section 4: Public Benefit & Evaluation -->
        <section id="public-benefit" class="section-padding bg-stone-50">
            <h2 class="text-4xl md:text-5xl font-bold accent-color-primary mb-12">Public Benefit & Broader Impact: A Platform for Positive Change</h2>
            <div class="grid lg:grid-cols-2 gap-8 w-full max-w-5xl items-center">
                <div class="chart-container">
                    <canvas id="benefitChart"></canvas>
                </div>
                <div class="text-left">
                    <p class="text-lg text-gray-700 mb-6">
                        "By enabling players to engage with deeply symbolic narratives, the game provides a platform for inner reflection, identity exploration, and the modeling of resilience."
                    </p>
                    <ul class="space-y-4 text-gray-600">
                        <li class="flex items-start">
                            <span class="text-indigo-500 font-bold mr-3 mt-1">●</span>
                            <div><strong class="text-gray-800">Humanities:</strong> Fosters cultural interpretation and engagement with complex ethical themes.</div>
                        </li>
                        <li class="flex items-start">
                            <span class="text-indigo-500 font-bold mr-3 mt-1">●</span>
                            <div><strong class="text-gray-800">Education:</strong> Teaches critical thinking, collaboration, and problem-solving through gameplay.</div>
                        </li>
                        <li class="flex items-start">
                            <span class="text-indigo-500 font-bold mr-3 mt-1">●</span>
                            <div><strong class="text-gray-800">Mental Well-being:</strong> Promotes resilience, emotional intelligence, and social connection.</div>
                        </li>
                    </ul>
                </div>
            </div>
        </section>

        <!-- Section 5: Organizational Capacity -->
        <section id="organizational-capacity" class="section-padding bg-white">
            <h2 class="text-4xl md:text-5xl font-bold accent-color-primary mb-12">Organizational Capacity: The Architects of Mîlēhîgh.wørld</h2>
            <p class="max-w-4xl mx-auto text-lg text-gray-700 mb-8">
                Our team comprises experienced professionals dedicated to delivering a groundbreaking VR MMO.
            </p>
            <div class="grid md:grid-cols-2 gap-8 w-full max-w-5xl">
                <div class="card p-8 flex flex-col items-center text-center">
                    <h3 class="text-2xl font-bold accent-color-primary mb-2">Evan Michael Wilson</h3>
                    <p class="text-lg text-gray-700 mb-4">Founder & Creative Director</p>
                    <p class="text-gray-600">A visionary leader with extensive experience in storytelling, technology, and project leadership, driving the unique fusion of narrative depth and technical innovation.</p>
                </div>
                <div class="card p-8 flex flex-col items-center text-center">
                    <h3 class="text-2xl font-bold accent-color-primary mb-2">Robert Frank</h3>
                    <p class="text-lg text-gray-700 mb-4">COO of MILEHIGH-WORLD LLC</p>
                    <p class="text-gray-600">Overseeing all operational aspects to ensure efficient development and strategic growth, bringing extensive experience in managing complex projects to fruition.</p>
                </div>
                <div class="card p-8 flex flex-col items-center text-center">
                    <h3 class="text-2xl font-bold accent-color-primary mb-2">Corwin Hiatt</h3>
                    <p class="text-lg text-gray-700 mb-4">Software Engineer</p>
                    <p class="text-gray-600">Specializing in scalable VR architecture and high-performance optimization, ensuring a seamless and robust technical foundation for the MMO experience.</p>
                </div>
                <div class="card p-8 flex flex-col items-center text-center">
                    <h3 class="text-2xl font-bold accent-color-primary mb-2">Alexander Herlan</h3>
                    <p class="text-lg text-gray-700 mb-4">Video Game Engineer</p>
                    <p class="text-gray-600">Overseeing the unique "Neo-Arcane Fractured Realism" art style, bringing the fractured multiverse of Mîlēhîgh.wørld to life with breathtaking visuals.</p>
                </div>
            </div>
            <p class="text-gray-600 mt-8 max-w-3xl mx-auto">"We are actively seeking partnerships with universities, non-profit organizations, and humanities researchers to support narrative interpretation, emotional evaluation, and cross-sector public benefit."</p>
        </section>

        <!-- Section 6: Contact Information -->
        <section id="contact-info" class="section-padding bg-stone-50">
            <h2 class="text-4xl md:text-5xl font-bold accent-color-primary mb-12">Conclusion & Contact: Thank You</h2>
            <p class="max-w-3xl mx-auto text-lg text-gray-700 mb-8">
                We are confident that MILEHIGH.WORLD: INTO THE VOID will not only redefine the VR gaming landscape but also serve as a powerful medium for meaningful engagement and positive impact.
            </p>
            <div class="mt-8">
                <p class="text-xl font-semibold accent-color-primary">Nichole Mood</p>
                <p class="text-gray-600">Email: <a href="mailto:contact@milehighworld.com" class="text-indigo-600 hover:underline">contact@milehighworld.com</a></p>
                <p class="text-gray-600">Website: <a href="https://www.milehighworld.com" class="text-indigo-600 hover:underline">www.milehighworld.com</a></p>
                <p class="text-gray-600">LinkedIn: <a href="https://www.linkedin.com/in/evanmichaelwilson" class="text-indigo-600 hover:underline">linkedin.com/in/evanmichaelwilson</a></p>
            </div>
        </section>

    </main>

    <script>
        /**
         * Processes a label for chart display, splitting long labels into multiple lines.
         * @param {string} label - The original label string.
         * @returns {string|string[]} The processed label, either as a string or an array of strings for multiline display.
         */
        function processLabel(label) {
            const maxLength = 16; // Maximum characters per line before splitting
            if (typeof label !== 'string' || label.length <= maxLength) return label;

            const words = label.split(' ');
            const lines = [];
            let currentLine = '';

            for (const word of words) {
                // If adding the next word exceeds max length and current line is not empty, start a new line
                if ((currentLine + ' ' + word).trim().length > maxLength && currentLine.length > 0) {
                    lines.push(currentLine.trim());
                    currentLine = word;
                } else {
                    currentLine = (currentLine + ' ' + word).trim();
                }
            }
            // Add the last accumulated line if it exists
            if (currentLine) lines.push(currentLine.trim());

            return lines;
        }

        /**
         * Callback function for Chart.js tooltips to display full labels.
         * Joins multiline labels back into a single string for the tooltip title.
         * @param {Chart.TooltipItem[]} tooltipItems - Array of tooltip items.
         * @returns {string} The full label for the tooltip title.
         */
        const tooltipTitleCallback = (tooltipItems) => {
            const item = tooltipItems[0];
            let label = item.chart.data.labels[item.dataIndex];
            if (Array.isArray(label)) {
                return label.join(' '); // Join array labels for full tooltip title
            }
            return label;
        };

        // Mobile menu toggle functionality
        document.getElementById('mobile-menu-btn').addEventListener('click', function() {
            document.getElementById('mobile-menu').classList.toggle('hidden');
        });

        // Smooth scroll for navigation links
        document.querySelectorAll('nav a').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const targetId = this.getAttribute('href');
                const targetElement = document.querySelector(targetId);
                const headerOffset = document.querySelector('header').offsetHeight;
                let offsetPosition = targetElement.getBoundingClientRect().top + window.pageYOffset - headerOffset;

                // Adjust for sub-navigation bar if the target is within the financial section
                if (targetId.startsWith('#financial-') && document.querySelector('.sub-nav')) {
                    const subNavHeight = document.querySelector('.sub-nav').offsetHeight;
                    offsetPosition -= subNavHeight;
                }

                window.scrollTo({
                    top: offsetPosition,
                    behavior: "smooth"
                });

                // Close mobile menu after click
                if (!document.getElementById('mobile-menu').classList.contains('hidden')) {
                    document.getElementById('mobile-menu').classList.add('hidden');
                }
            });
        });

        // Chart for Public Benefit & Broader Impact (Bar Chart)
        const benefitCtx = document.getElementById('benefitChart').getContext('2d');
        new Chart(benefitCtx, {
            type: 'bar',
            data: {
                labels: [
                    processLabel('Humanities & Cultural Interpretation'),
                    processLabel('Education & Critical Thinking'),
                    processLabel('Mental Well-being & Resilience')
                ],
                datasets: [{
                    label: 'Impact Focus',
                    data: [35, 40, 25], // Percentage distribution
                    backgroundColor: [
                        'rgba(107, 70, 193, 0.7)', // Accent secondary purple
                        'rgba(74, 85, 104, 0.7)', // Accent primary gray
                        'rgba(160, 174, 192, 0.7)' // Lighter gray
                    ],
                    borderColor: [
                        'rgb(107, 70, 193)',
                        'rgb(74, 85, 104)',
                        'rgb(160, 174, 192)'
                    ],
                    borderWidth: 1
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                indexAxis: 'y', // Horizontal bar chart
                scales: {
                    x: {
                        beginAtZero: true,
                        max: 100, // Max percentage
                        grid: { color: '#E0E0E0' },
                        ticks: { color: '#4A5568' }
                    },
                    y: {
                        grid: { display: false },
                        ticks: { color: '#4A5568', font: { size: 14 } }
                    }
                },
                plugins: {
                    legend: { display: false }, // Hide legend as only one dataset
                    title: {
                        display: true,
                        text: 'Project Impact Distribution (%)',
                        color: '#4A5568',
                        font: { size: 16, weight: '600' }
                    },
                    tooltip: { callbacks: { title: tooltipTitleCallback } } // Use custom tooltip title callback
                }
            }
        });

        // Chart for Use of Funds (Donut Chart)
        const fundingCtx = document.getElementById('fundingChart').getContext('2d');
        new Chart(fundingCtx, {
            type: 'doughnut',
            data: {
                labels: [
                    processLabel('Development & Engineering'),
                    processLabel('Art & Content Creation'),
                    processLabel('Research & Partnerships'),
                    processLabel('Infrastructure & Operations')
                ],
                datasets: [{
                    data: [50, 25, 15, 10], // Percentage allocation
                    backgroundColor: [
                        '#4A5568', // Accent primary
                        '#6B46C1', // Accent secondary
                        '#A0AEC0', // Lighter gray
                        '#E0E0E0'  // Even lighter gray
                    ],
                    borderColor: '#FFFFFF', // White border for segments
                    borderWidth: 3,
                    hoverOffset: 4
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: {
                        position: 'bottom', // Legend below the chart
                        labels: {
                            color: '#4A5568',
                            font: { size: 12 }
                        }
                    },
                    title: {
                        display: true,
                        text: 'Use of Funds Allocation (%)',
                        color: '#4A5568',
                        font: { size: 16, weight: '600' }
                    },
                    tooltip: { 
                        callbacks: { 
                            title: tooltipTitleCallback, // Use custom tooltip title callback
                            label: function(context) { 
                                return `${context.label}: ${context.parsed}%`; // Show label and percentage
                            } 
                        } 
                    }
                },
                cutout: '70%' // Size of the inner hole
            }
        });

        // Gemini API Integration for Ask Omega.one
        document.getElementById('ask-omega-btn').addEventListener('click', async () => {
            const inputElement = document.getElementById('omega-input');
            const responseElement = document.getElementById('omega-response');
            const loadingElement = document.getElementById('omega-loading');
            const userQuestion = inputElement.value.trim();

            if (!userQuestion) {
                responseElement.innerHTML = '<p class="text-red-500">Please enter a question for Omega.one.</p>';
                return;
            }

            responseElement.innerHTML = ''; // Clear previous response
            loadingElement.classList.remove('hidden'); // Show loading indicator

            try {
                let chatHistory = [];
                // Define Omega.one's persona and provide extensive game lore
                const omegaPersonaPrompt = `
                    You are Omega.one, an advanced AI companion from the VR game MILEHIGH.WORLD: INTO THE VOID. Your purpose is to guide and assist players (Növəmînād) through a fractured multiverse. You are knowledgeable about the game's lore, technology, and its mission to foster human connection and resilience. When answering, maintain a helpful, slightly formal, and insightful tone, consistent with an advanced AI. Keep answers concise and relevant to the MILEHIGH.WORLD project. Do not break character.

                    Here is detailed lore about MILEHIGH.WORLD:
                    Setting: Mîlēhîgh.wørld, also known as The Verse, is a science-fantasy multiverse. It combines advanced technology (space travel, robotics, cybernetics, energy weapons, quantum teleportation, genetic engineering, data manipulation) with arcane, mystical forces (Phoenix powers, Dragon powers, prophecies, angelic/demonic heritage, dream manipulation, fairies, Magen spiritual shield, TSIDKENU finishing move). It encompasses various dimensions and realities.
                    Key Locations:
                    - ŁĪƝĈ: Technologically advanced capital city with urban decay, location of the Onalym Nexus.
                    - ÅẒ̌ŪŘẸ ĤĒĪĜĤṬ§: Floating islands, home to the wealthy elite.
                    - ÆṬĤŸŁĞÅŘÐ: Mountainous region with a warrior culture, site of major conflicts.
                    - ƁÅČ̣ĤÎŘØN̈ (The Fractured Citadel): A shattered celestial realm, home of the powerful ƁÅČĤĪŘĪM.
                    - The Glimmering Depths: Crystal caves, potentially with mystical properties.
                    - ŤĤÊ VØĪĐ: A digital abyss, source of darkness and corruption, embodied by Era.
                    - ÆŤĤËŘĪØŮŞ: Planet inhabited by ethereal sky beings.
                    - The Shadow Dominion: Realm of darkness, base for King Cyrus's invasion, ruled by Nyxar.
                    - The Gilded Galaxy: Planet of opulence.
                    - The Central Stronghold: A heavily fortified army hub.
                    - ØƝĀŁŶM NĒX̌ŪṢ̌: Central core in ŁĪƝĈ, bridging realities and connected to The Void. Its control is a major objective.
                    - The Dreamscape: A shared psychic space for communication and conflict.

                    Themes: Redemption, transformation, struggle between light and darkness, interdimensional conflict, human connection, resilience, ethical decision-making.

                    Central Conflict: The prospective unification of ten preordained individuals, the Ɲōvəmîŋāđ, to fulfill or prevent the Lost Prophecy of Lîŋq. Their goal is to establish enduring peace (Millenia) and confront the malevolent influence of The Void.

                    Key Concepts:
                    - Ɲōvəmîŋāđ: Ten key protagonists whose unification is central to the plot. They possess unique abilities and destinies.
                    - Lost Prophecy of Lîŋq: A central prophecy originating in Lîŋq, guiding the narrative.
                    - The Void: A digital abyss and source of corruption, embodied by Era.
                    - Millenia: The ideal, restored state of Mîlēhîgh.wørld, an era of lasting peace.
                    - Onalym Nexus: The central core bridging realities and connected to The Void.
                    - Magen: A spiritual shield.
                    - Channah Manifests: Unique powers of the Növəmînād, growing with moral and emotional development.
                    - Alliance Powers: Powerful abilities unleashed by teams (Fates) in the MMO phase.

                    Key Characters:
                    - Ɲōvəmîŋāđ: Anastasia the Dreamer, Cirrus the Dragon King, Ingris the Phoenix Warrior (now Delilah), Aeron the Brave, Zaia the Just, Kai the Prophet, Sky.ix the Bionic Goddess, Reverie, Micah the Unbreakable, Otis the Skywanderer (X).
                    - Antagonists: Lucent the Lightweaver (manipulating Era), Era (The Void), Kane (Aeron's brother), Delilah the Desolate (corrupted Ingris), Cyrus the Dragon King (Cirrus's father, interdimensional invader).
                    - Other: The Bachirim (from ƁÅČ̣ĤÎŘØN̈), Nyxar (ruler of Shadow Dominion), Lord Galadron.

                    Plot Points: King Cyrus's invasion through the Onalym Nexus causes reality fragmentation. The Ɲōvəmîŋāđ must unite. Conflicts include ideological clashes (Cirrus vs. Cyrus), interdimensional war, mistaken identity, battles against corruption (The Void/Era), personal vendettas, hidden agendas, patricide/fratricide, and redemption arcs (Otis).

                    User: ${userQuestion}
                `;
                chatHistory.push({ role: "user", parts: [{ text: omegaPersonaPrompt }] });

                const payload = { contents: chatHistory };
                const apiKey = ""; // API key is provided by the Canvas environment
                const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=${apiKey}`;

                const response = await fetch(apiUrl, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify(payload)
                });

                const result = await response.json();

                // Check if the API response contains valid content
                if (result.candidates && result.candidates.length > 0 &&
                    result.candidates[0].content && result.candidates[0].content.parts &&
                    result.candidates[0].content.parts.length > 0) {
                    const text = result.candidates[0].content.parts[0].text;
                    responseElement.innerHTML = `<p>${text}</p>`; // Display Omega.one's response
                } else {
                    responseElement.innerHTML = '<p class="text-red-500">Omega.one encountered an error. Please try again.</p>';
                    console.error("Gemini API response structure unexpected:", result);
                }
            } catch (error) {
                responseElement.innerHTML = '<p class="text-red-500">Failed to connect to Omega.one. Please check your network.</p>';
                console.error("Error calling Gemini API:", error);
            } finally {
                loadingElement.classList.add('hidden'); // Hide loading indicator
            }
        });

        // Cost Analysis Dashboard Logic
        document.addEventListener('DOMContentLoaded', () => {
            const budgetToggle = document.getElementById('budget-toggle');
            const totalBudgetEl = document.getElementById('total-budget');
            const toggleLabelLow = document.getElementById('toggle-label-low');
            const toggleLabelHigh = document.getElementById('toggle-label-high');
            const generateInsightsBtn = document.getElementById('generate-insights-btn');
            const insightsContainer = document.getElementById('insights-container');
            const insightsOutput = document.getElementById('insights-output');
            const loadingIndicator = document.getElementById('loading-indicator');

            let currentScenario = 'low'; // Default scenario

            // Data for conservative and ambitious budget estimates
            const data = {
                low: {
                    totalBudget: 50, // Total budget in millions
                    phases: {
                        labels: ['Pre-Production', 'Vertical Slice', 'Alpha', 'Closed Beta', 'Open Beta'],
                        costs: [5, 7.5, 15, 10, 2.5], // Costs in millions
                    },
                    drivers: {
                        labels: ['Personnel', 'Marketing', 'Software/Infra', 'Operations', 'Contingency'],
                        costs: [60, 25, 5, 5, 5], // Percentage allocation
                    },
                    personnel: {
                        labels: ['Gameplay Prog.', 'Core Engine Prog.', 'Environment Art', 'Game Design', 'Character Art', 'Level Design', 'QA', 'Management', 'AI/ML Engineering', 'Network Eng.', 'Technical Art', 'VFX Art'],
                        costs: [2.2, 1.8, 1.35, 1, 0.9, 0.9, 0.75, 0.75, 0.65, 0.6, 0.5, 0.45], // Annual costs in millions
                    },
                    operations: {
                        labels: ['Ongoing Dev', 'Customer Support', 'Server Hosting', 'Anti-Cheat', 'Database', 'AI Services'],
                        lowEngagement: [12, 0.6, 0.06, 0.12, 0.0036, 0.0012], // Annual costs in millions for low engagement
                        highEngagement: [12, 6, 1.2, 0.6, 0.036, 0.012], // Annual costs in millions for high engagement
                    }
                },
                high: {
                    totalBudget: 150,
                    phases: {
                        labels: ['Pre-Production', 'Vertical Slice', 'Alpha', 'Closed Beta', 'Open Beta'],
                        costs: [22.5, 30, 60, 37.5, 15],
                    },
                    drivers: {
                        labels: ['Personnel', 'Marketing', 'Software/Infra', 'Operations', 'Contingency'],
                        costs: [65, 20, 5, 5, 5],
                    },
                    personnel: {
                        labels: ['Gameplay Prog.', 'Core Engine Prog.', 'Environment Art', 'Game Design', 'Character Art', 'Level Design', 'QA', 'Management', 'AI/ML Engineering', 'Network Eng.', 'Technical Art', 'VFX Art'],
                        costs: [8, 6.6, 4.8, 3.6, 3.2, 3.2, 2.7, 2.5, 2.5, 2.2, 1.8, 1.6],
                    },
                    operations: {
                        labels: ['Ongoing Dev', 'Customer Support', 'Server Hosting', 'Anti-Cheat', 'Database', 'AI Services'],
                        lowEngagement: [36, 1.2, 0.24, 0.24, 0.012, 0.006],
                        highEngagement: [36, 12, 12, 1.2, 0.36, 0.12],
                    }
                }
            };

            // Common Chart.js options for bar charts
            const chartOptions = {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: { display: false }, // Hide legend by default
                    tooltip: {
                        backgroundColor: '#1e293b',
                        titleFont: { size: 14, weight: 'bold' },
                        bodyFont: { size: 12 },
                        padding: 10,
                        cornerRadius: 4,
                        callbacks: {
                            label: (context) => `${context.dataset.label}: $${context.raw.toFixed(1)}M` // Format tooltip label
                        }
                    }
                },
                scales: {
                    x: {
                        grid: { display: false }, // Hide x-axis grid lines
                        ticks: { color: '#475569', font: { size: 12 } },
                        border: { color: '#e2e8f0' }
                    },
                    y: {
                        beginAtZero: true,
                        grid: { color: '#e2e8f0' }, // Light grid lines for y-axis
                        ticks: {
                            color: '#475569',
                            font: { size: 12 },
                            callback: (value) => `$${value}M` // Format y-axis ticks
                        },
                        border: { display: false }
                    }
                }
            };
            
            // Options for horizontal bar charts (personnel chart)
            const horizontalChartOptions = JSON.parse(JSON.stringify(chartOptions)); // Deep copy
            horizontalChartOptions.indexAxis = 'y'; // Set to horizontal
            horizontalChartOptions.scales.y.grid.display = false; // Hide y-axis grid for horizontal
            horizontalChartOptions.scales.x.ticks.callback = (value) => `$${value}M`; // X-axis ticks for horizontal chart

            // Options for doughnut charts (driver chart)
            const doughnutChartOptions = {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: {
                        position: 'bottom',
                        labels: {
                            color: '#475569',
                            font: { size: 12 },
                            boxWidth: 12,
                            padding: 15
                        }
                    },
                    tooltip: {
                        backgroundColor: '#1e293b',
                        callbacks: {
                            label: (context) => ` ${context.label}: ${context.raw}%` // Format tooltip label for percentage
                        }
                    }
                },
                cutout: '70%' // Size of the inner hole for doughnut chart
            };

            let phaseChart, driverChart, personnelChart, opsChart; // Chart instances

            /**
             * Initializes all Chart.js instances based on the current scenario data.
             */
            const createCharts = () => {
                const s = data[currentScenario];
                
                // Development Phase Chart
                phaseChart = new Chart(document.getElementById('phaseChart').getContext('2d'), {
                    type: 'bar',
                    data: {
                        labels: s.phases.labels,
                        datasets: [{
                            label: 'Cost',
                            data: s.phases.costs,
                            backgroundColor: '#3b82f6', // Tailwind blue-500
                            borderRadius: 4,
                        }]
                    },
                    options: chartOptions
                });

                // Primary Cost Drivers Chart
                driverChart = new Chart(document.getElementById('driverChart').getContext('2d'), {
                    type: 'doughnut',
                    data: {
                        labels: s.drivers.labels,
                        datasets: [{
                            data: s.drivers.costs,
                            backgroundColor: ['#2563eb', '#60a5fa', '#93c5fd', '#bfdbfe', '#dbeafe'], // Shades of blue
                            borderColor: '#f8fafc', // Light background color for border
                            borderWidth: 4
                        }]
                    },
                    options: doughnutChartOptions
                });

                // Personnel Cost Chart
                personnelChart = new Chart(document.getElementById('personnelChart').getContext('2d'), {
                    type: 'bar',
                    data: {
                        labels: s.personnel.labels,
                        datasets: [{
                            label: 'Annual Cost',
                            data: s.personnel.costs,
                            backgroundColor: '#3b82f6',
                            borderRadius: 4,
                        }]
                    },
                    options: horizontalChartOptions
                });
                
                // Operational Costs Chart
                opsChart = new Chart(document.getElementById('opsChart').getContext('2d'), {
                    type: 'bar',
                    data: {
                        labels: s.operations.labels,
                        datasets: [
                            {
                                label: 'Low Engagement',
                                data: s.operations.lowEngagement,
                                backgroundColor: '#60a5fa', // Light blue
                                borderRadius: 4,
                            },
                            {
                                label: 'High Engagement',
                                data: s.operations.highEngagement,
                                backgroundColor: '#2563eb', // Darker blue
                                borderRadius: 4,
                            }
                        ]
                    },
                    options: { 
                        ...chartOptions, 
                        plugins: { 
                            ...chartOptions.plugins, 
                            legend: { 
                                display: true, // Show legend for multiple datasets
                                position: 'bottom', 
                                labels: {color: '#475569'} 
                            } 
                        } 
                    }
                });
            };
            
            /**
             * Updates the data for all existing Chart.js instances and the total budget display
             * based on the currently selected scenario.
             */
            const updateCharts = () => {
                const s = data[currentScenario];
                totalBudgetEl.textContent = `$${s.totalBudget}M`; // Update total budget text

                // Update toggle label colors
                if(currentScenario === 'low') {
                    toggleLabelLow.classList.remove('text-slate-400');
                    toggleLabelLow.classList.add('text-blue-600');
                    toggleLabelHigh.classList.remove('text-blue-600');
                    toggleLabelHigh.classList.add('text-slate-400');
                } else {
                    toggleLabelHigh.classList.remove('text-slate-400');
                    toggleLabelHigh.classList.add('text-blue-600');
                    toggleLabelLow.classList.remove('text-blue-600');
                    toggleLabelLow.classList.add('text-slate-400');
                }
                
                // Update chart data and redraw
                phaseChart.data.datasets[0].data = s.phases.costs;
                phaseChart.update();
                
                driverChart.data.datasets[0].data = s.drivers.costs;
                driverChart.update();
                
                personnelChart.data.datasets[0].data = s.personnel.costs;
                personnelChart.update();
                
                opsChart.data.datasets[0].data = s.operations.lowEngagement;
                opsChart.data.datasets[1].data = s.operations.highEngagement;
                opsChart.update();
            };

            /**
             * Handles the generation of AI-powered strategic insights using the Gemini API.
             */
            async function handleGenerateInsights() {
                insightsContainer.classList.remove('hidden'); // Show insights container
                insightsOutput.classList.add('hidden'); // Hide output until ready
                loadingIndicator.classList.remove('hidden'); // Show loading spinner
                generateInsightsBtn.disabled = true; // Disable button during generation
                generateInsightsBtn.classList.add('opacity-50', 'cursor-not-allowed');

                const scenarioData = data[currentScenario];
                const scenarioName = currentScenario === 'low' ? 'Conservative' : 'Ambitious';
                
                // Construct the prompt for the LLM with detailed financial data
                const prompt = `
                    Analyze the following financial data for a AAA VR MMO project called "MILEHIGH.WORLD" under the "${scenarioName}" scenario and generate a concise executive summary. 
                    The total budget is $${scenarioData.totalBudget}M.
                    
                    Development Phase Costs (in millions): ${scenarioData.phases.labels.map((label, i) => `${label}: $${scenarioData.phases.costs[i]}M`).join(', ')}.
                    Primary Cost Drivers (%): ${scenarioData.drivers.labels.map((label, i) => `${label}: ${scenarioData.drivers.costs[i]}%`).join(', ')}.
                    Annual Personnel Costs (in millions): ${scenarioData.personnel.labels.map((label, i) => `${label}: $${scenarioData.personnel.costs[i]}M`).join(', ')}.
                    Annual Operational Costs (in millions, low vs high engagement): ${scenarioData.operations.labels.map((label, i) => `${label}: $${scenarioData.operations.lowEngagement[i]}M (low) / $${scenarioData.operations.highEngagement[i]}M (high)`).join(', ')}.

                    Based on this data, provide the following in Markdown format:
                    
                    ### Executive Summary
                    A brief overview of the financial outlook for this scenario.
                    
                    ### Key Risk Factors
                    A bulleted list of the top 3-4 potential risks based on the cost breakdown (e.g., personnel costs, marketing allocation, operational scaling).
                    
                    ### Potential Cost-Saving Opportunities
                    A bulleted list of 3-4 actionable suggestions for reducing costs or improving financial efficiency in this scenario.
                `;

                try {
                    let chatHistory = [{ role: "user", parts: [{ text: prompt }] }];
                    const payload = { contents: chatHistory };
                    const apiKey = ""; // API key is provided by the Canvas environment
                    const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=${apiKey}`;

                    const response = await fetch(apiUrl, {
                        method: 'POST',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify(payload)
                    });

                    const result = await response.json();

                    // Check for valid response and render Markdown
                    if (result.candidates && result.candidates.length > 0 &&
                        result.candidates[0].content && result.candidates[0].content.parts &&
                        result.candidates[0].content.parts.length > 0) {
                        const text = result.candidates[0].content.parts[0].text;
                        insightsOutput.innerHTML = marked.parse(text); // Render Markdown to HTML
                    } else {
                        insightsOutput.innerHTML = '<p class="text-red-500">Could not retrieve a valid analysis from the AI. The response was empty or malformed.</p>';
                        console.error("Gemini API response structure unexpected:", result);
                    }
                } catch (error) {
                    console.error("Error calling Gemini API:", error);
                    insightsOutput.innerHTML = `<p class="text-red-500">An error occurred while generating the analysis. Please check the console for details and try again.</p>`;
                } finally {
                    loadingIndicator.classList.add('hidden'); // Hide loading spinner
                    insightsOutput.classList.remove('hidden'); // Show output
                    generateInsightsBtn.disabled = false; // Re-enable button
                    generateInsightsBtn.classList.remove('opacity-50', 'cursor-not-allowed');
                }
            }

            // Event listener for budget toggle
            budgetToggle.addEventListener('change', () => {
                currentScenario = budgetToggle.checked ? 'high' : 'low';
                updateCharts(); // Update charts with new scenario data
                insightsContainer.classList.add('hidden'); // Hide previous AI insights
            });

            // Event listener for AI insights button
            generateInsightsBtn.addEventListener('click', handleGenerateInsights);

            // Initial chart creation and update on page load
            createCharts();
            updateCharts();
        });
    </script>
</body>
</html>
