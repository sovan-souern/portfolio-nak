<template>
  <div class="min-h-screen bg-gradient-to-br from-slate-50 to-blue-50">
    <!-- Navigation -->
    <nav class="fixed top-0 w-full bg-white/90 backdrop-blur-lg border-b border-slate-200/50 z-50 shadow-sm">
      <div class="max-w-6xl mx-auto px-6 py-4">
        <div class="flex items-center justify-between">
          <!-- Enhanced logo with gradient text -->
          <div class="font-bold text-xl bg-gradient-to-r from-blue-600 to-teal-600 bg-clip-text text-transparent">
            Channak Kan
          </div>
          <div class="hidden md:flex space-x-8">
            <a href="#about" class="text-slate-600 hover:text-blue-600 transition-all duration-300 font-medium">About</a>
            <a href="#skills" class="text-slate-600 hover:text-blue-600 transition-all duration-300 font-medium">Skills</a>
            <a href="#projects" class="text-slate-600 hover:text-blue-600 transition-all duration-300 font-medium">Projects</a>
            <a href="#contact" class="text-slate-600 hover:text-blue-600 transition-all duration-300 font-medium">Contact</a>
          </div>
        </div>
      </div>
    </nav>

    <!-- Hero Section -->
    <!-- Enhanced hero with better gradients and animations -->
    <section class="pt-32 pb-20 px-6 relative overflow-hidden">
      <!-- Background decoration -->
      <div class="absolute inset-0 bg-gradient-to-br from-blue-50 via-white to-teal-50"></div>
      <div class="absolute top-20 right-10 w-72 h-72 bg-gradient-to-br from-blue-200/30 to-teal-200/30 rounded-full blur-3xl"></div>
      <div class="absolute bottom-20 left-10 w-96 h-96 bg-gradient-to-br from-teal-200/20 to-blue-200/20 rounded-full blur-3xl"></div>
      
      <div class="max-w-6xl mx-auto relative">
        <div class="text-center">
          <!-- Enhanced profile image with better styling -->
          <div class="relative inline-block mb-8">
            <div class="w-36 h-36 bg-gradient-to-br from-blue-500 via-blue-600 to-teal-600 rounded-full p-1 shadow-2xl">
              <!-- Fixed profile image path to use public folder -->
              <img src="../assets/img/nak.jpg" alt="Profile" class="rounded-full w-full h-full object-cover border-4 border-white" 
                   @error="handleImageError" />
            </div>
            <div class="absolute -bottom-2 -right-2 w-8 h-8 bg-green-500 rounded-full border-4 border-white"></div>
          </div>
          
          <!-- Enhanced typography with gradient text -->
          <h1 class="text-5xl md:text-7xl font-bold mb-6 text-balance">
            <span class="bg-gradient-to-r from-slate-900 via-blue-900 to-teal-900 bg-clip-text text-transparent">
              {{ name }}
            </span>
          </h1>
          <p class="text-xl md:text-2xl text-slate-600 mb-10 max-w-3xl mx-auto text-pretty font-light">
            {{ tagline }}
          </p>
          
          <!-- Enhanced buttons with better styling -->
          <div class="flex flex-col sm:flex-row gap-4 justify-center">
            <button @click="scrollToSection('projects')"
              class="group bg-gradient-to-r from-blue-600 to-teal-600 text-white px-10 py-4 rounded-xl font-semibold hover:shadow-xl hover:scale-105 transition-all duration-300 flex items-center justify-center gap-2">
              <span>View My Work</span>
              <svg class="w-5 h-5 group-hover:translate-x-1 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"></path>
              </svg>
            </button>
            <button @click="scrollToSection('contact')"
              class="border-2 border-slate-300 text-slate-700 px-10 py-4 rounded-xl font-semibold hover:bg-slate-50 hover:border-slate-400 hover:scale-105 transition-all duration-300">
              Get In Touch
            </button>
          </div>
        </div>
      </div>
    </section>


    <!-- About Section -->
    <!-- Enhanced about section with better cards and layout -->
    <section id="about" class="py-20 px-6 bg-white">
      <div class="max-w-5xl mx-auto">
        <h2 class="text-4xl font-bold text-slate-900 mb-12 text-center">About Me</h2>
        <div class="grid md:grid-cols-2 gap-16 items-center">
          <div class="space-y-6">
            <p class="text-slate-600 text-lg leading-relaxed">
              {{ aboutText }}
            </p>
            <div class="flex flex-wrap gap-3">
              <span v-for="interest in interests" :key="interest"
                class="bg-gradient-to-r from-blue-50 to-teal-50 text-slate-700 px-4 py-2 rounded-full text-sm font-medium border border-blue-100 hover:shadow-md transition-shadow">
                {{ interest }}
              </span>
            </div>
          </div>
          <div class="bg-gradient-to-br from-slate-50 to-blue-50 rounded-3xl p-8 shadow-lg border border-slate-100">
            <h3 class="font-bold text-slate-900 mb-6 text-xl">Quick Facts</h3>
            <div class="space-y-4">
              <div class="flex justify-between items-center p-3 bg-white rounded-xl">
                <span class="text-slate-600 font-medium">Experience</span>
                <span class="font-bold text-blue-600">{{ experience }}</span>
              </div>
              <div class="flex justify-between items-center p-3 bg-white rounded-xl">
                <span class="text-slate-600 font-medium">Location</span>
                <span class="font-bold text-slate-900">{{ location }}</span>
              </div>
              <div class="flex justify-between items-center p-3 bg-white rounded-xl">
                <span class="text-slate-600 font-medium">Focus</span>
                <span class="font-bold text-teal-600">{{ focus }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Skills Section -->
    <!-- Enhanced skills with better visual indicators and cards -->
    <section id="skills" class="py-20 px-6 bg-gradient-to-br from-slate-50 to-blue-50">
      <div class="max-w-5xl mx-auto">
        <h2 class="text-4xl font-bold text-slate-900 mb-16 text-center">Skills & Technologies</h2>
        <div class="grid md:grid-cols-3 gap-8">
          <div v-for="category in skillCategories" :key="category.name" 
            class="bg-white rounded-2xl p-8 shadow-lg hover:shadow-xl transition-all duration-300 border border-slate-100 hover:scale-105">
            <h3 class="font-bold text-slate-900 mb-6 text-xl text-center">{{ category.name }}</h3>
            <div class="space-y-4">
              <div v-for="skill in category.skills" :key="skill.name" class="space-y-2">
                <div class="flex items-center justify-between">
                  <span class="text-slate-700 font-medium">{{ skill.name }}</span>
                  <span class="text-sm text-slate-500">{{ skill.level }}/5</span>
                </div>
                <!-- Better progress bars instead of dots -->
                <div class="w-full bg-slate-200 rounded-full h-2">
                  <div class="bg-gradient-to-r from-blue-500 to-teal-500 h-2 rounded-full transition-all duration-500"
                    :style="{ width: (skill.level / 5) * 100 + '%' }"></div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>


    <!-- Projects Section -->
    <!-- Enhanced project cards with better visuals and hover effects -->
    <section id="projects" class="py-20 px-6 bg-white">
      <div class="max-w-6xl mx-auto">
        <h2 class="text-4xl font-bold text-slate-900 mb-16 text-center">School Projects</h2>
        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div v-for="project in projects" :key="project.id"
            class="group bg-white rounded-2xl overflow-hidden shadow-lg hover:shadow-2xl transition-all duration-300 border border-slate-100 hover:scale-105">
            <!-- Updated project image implementation with better error handling -->
            <div class="h-48 relative overflow-hidden">
              <img 
                v-if="project.image && !project.imageError" 
                :src="project.image" 
                :alt="project.name"
                class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-300"
                @error="() => handleProjectImageError(project)"
                @load="() => handleProjectImageLoad(project)"
              />
              <!-- Fallback gradient background if no image or image fails to load -->
              <div v-else class="h-full bg-gradient-to-br from-blue-500 via-blue-600 to-teal-500 flex items-center justify-center relative">
                <div class="absolute inset-0 bg-gradient-to-br from-blue-400/20 to-teal-400/20"></div>
                <div class="text-white text-4xl font-bold z-10">{{ project.name.charAt(0) }}</div>
                <div class="absolute top-4 right-4 w-3 h-3 bg-white/30 rounded-full"></div>
                <div class="absolute bottom-4 left-4 w-2 h-2 bg-white/20 rounded-full"></div>
              </div>
              <!-- Overlay for better text readability on images -->
              <div class="absolute inset-0 bg-gradient-to-t from-black/20 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
            </div>
            <div class="p-6">
              <h3 class="font-bold text-slate-900 mb-3 text-lg group-hover:text-blue-600 transition-colors">{{ project.name }}</h3>
              <p class="text-slate-600 mb-4 leading-relaxed">{{ project.description }}</p>
              <div class="flex flex-wrap gap-2 mb-6">
                <span v-for="tech in project.technologies" :key="tech"
                  class="bg-gradient-to-r from-slate-100 to-blue-50 text-slate-700 px-3 py-1 rounded-full text-xs font-medium border border-slate-200">
                  {{ tech }}
                </span>
              </div>
              <div class="flex gap-4">
                <a :href="project.liveUrl" 
                  class="text-blue-600 hover:text-blue-700 font-semibold flex items-center gap-1 group/link">
                  <span>Live Demo</span>
                  <svg class="w-4 h-4 group-hover/link:translate-x-1 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"></path>
                  </svg>
                </a>
                <a :href="project.githubUrl" 
                  class="text-slate-600 hover:text-slate-800 font-semibold flex items-center gap-1">
                  <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24">

                    <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
                  </svg>
                  <span>GitHub</span>
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <!-- Enhanced contact section with better styling and gradients -->
    <section id="contact" class="py-20 px-6 bg-gradient-to-br from-slate-900 via-blue-900 to-slate-900 relative overflow-hidden">
      <!-- Background decoration -->
      <div class="absolute top-0 left-1/4 w-96 h-96 bg-blue-500/10 rounded-full blur-3xl"></div>
      <div class="absolute bottom-0 right-1/4 w-72 h-72 bg-teal-500/10 rounded-full blur-3xl"></div>
      
      <div class="max-w-4xl mx-auto text-center relative">
        <h2 class="text-4xl font-bold text-white mb-8">Let's Work Together</h2>
        <p class="text-xl text-slate-300 mb-12 max-w-2xl mx-auto leading-relaxed">
          I'm always interested in new opportunities and collaborations.
          Feel free to reach out if you'd like to discuss a project or just say hello!
        </p>
        <div class="flex flex-col sm:flex-row gap-6 justify-center mb-12">
          <a href="tel:+85560833842"
            class="group bg-gradient-to-r from-blue-600 to-teal-600 text-white px-10 py-4 rounded-xl font-semibold hover:shadow-2xl hover:scale-105 transition-all duration-300 flex items-center justify-center gap-3">
            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"></path>
            </svg>
            <span>060 833 842</span>
          </a>
          <a href="https://www.linkedin.com/in/channak-kan-11a970344/" target="_blank" rel="noopener noreferrer"
            class="border-2 border-slate-600 text-slate-300 px-10 py-4 rounded-xl font-semibold hover:bg-slate-800 hover:border-slate-500 hover:scale-105 transition-all duration-300 flex items-center justify-center gap-3">
            <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
              <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
            </svg>
            <span>LinkedIn</span>
          </a>
        </div>
        <div class="flex justify-center space-x-8">
          <a href="https://github.com/Channak18" class="text-slate-400 hover:text-white transition-colors flex items-center gap-2 group">
            <svg class="w-6 h-6 group-hover:scale-110 transition-transform" fill="currentColor" viewBox="0 0 24 24">

              <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
            </svg>
            <span>GitHub</span>
          </a>
          <a href="https://www.linkedin.com/in/channak-kan-11a970344/" class="text-slate-400 hover:text-white transition-colors flex items-center gap-2 group">
            <svg class="w-6 h-6 group-hover:scale-110 transition-transform" fill="currentColor" viewBox="0 0 24 24">
              <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
            </svg>
            <span>LinkedIn</span>
          </a>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

// Personal Information
const name = ref('Channak Kan')
const tagline = ref('Frontend Developer & Quality Assurance Tester')
const aboutText = ref('My name is Channak Kan, a web development student at Passerelles Numériques Cambodia. I am passionate about creating beautiful and functional web applications that provide excellent user experiences. With a strong foundation in both frontend and backend technologies, I enjoy tackling complex problems and turning ideas into reality.')
const experience = ref('2 Years')
const location = ref('Sen Sok, Phnom Penh')
const focus = ref('Web Development')
const email = ref('john@example.com')
const githubUrl = ref('https://github.com/johndoe')
const linkedinUrl = ref('https://linkedin.com/in/johndoe')
const twitterUrl = ref('https://twitter.com/johndoe')

const initials = computed(() => {
  return name.value.split(' ').map(n => n[0]).join('')
})

const interests = ref([
  'HTML', 'CSS', 'JavaScript', 'SASS', 'Vue.js', 'Node.js (Basic Rest API)', 'Database(MySQL)', 'MS Office (Word, Excel, PowerPoint)'
])

// Skills Data
const skillCategories = ref([
  {
    name: 'Frontend',
    skills: [
      { name: 'HTML', level: 5 },
      { name: 'CSS', level: 5 },
      { name: 'JavaScript', level: 4 },
      { name: 'SASS', level: 2 },
      { name: 'Vue.js', level: 4 },
      { name: 'Tailwind CSS', level: 4 }
    ]
  },
  {
    name: 'Backend',
    skills: [
      { name: 'Node.js', level: 4 },
      { name: 'Laravel', level: 4 },
      { name: 'Database (MySQL)', level: 4 },
      { name: 'OOP with TypeScript', level: 3 }
    ]
  },
  {
    name: 'Tools',
    skills: [
      { name: 'Git', level: 5 },
      { name: 'GitHub', level: 4 },
      { name: 'Jira', level: 4 },
      { name: 'Postman', level: 4 },
      { name: 'Figma', level: 4 },
      { name: 'Canva', level: 4 },
      { name: 'VS Code', level: 5 },
    ]
  }
])


// Projects Data
const projects = ref([
  {
    id: 1,
    name: 'POS System',
    description: 'Role: Frontend developer & QA tester',
    technologies: ['HTML', 'CSS', 'JavaScript', 'PHP', 'Database (MySQL)'],
    liveUrl: 'https://example.com',
    githubUrl: 'https://github.com/sinhpp/VC1-POS_System',
    image: 'https://images.unsplash.com/photo-1611224923853-80b023f02d71?w=400&h=200&fit=crop',
    imageError: false
  },
  {
    id: 2,
    name: 'Task Management App',
    description: 'Personal project developed using Vue.js.',
    technologies: ['Vue.js', 'Tailwind CSS'],
    liveUrl: 'https://melodic-sundae-83a3eb.netlify.app/',
    githubUrl: 'https://github.com/johndoe/taskapp',
    image: 'https://images.unsplash.com/photo-1611224923853-80b023f02d71?w=400&h=200&fit=crop',
    imageError: false
  },
  {
    id: 3,
    name: 'Static Website',
    description: 'Personal project developed using Vue.js.',
    technologies: ['Vue.js', 'Tailwind CSS'],
    liveUrl: 'https://dream-home-six.vercel.app/',
    githubUrl: 'https://github.com/Channak18/DreamHome',
    image: 'https://images.unsplash.com/photo-1560472354-b33ff0c44a43?w=400&h=200&fit=crop',
    imageError: false
  },
  {
    id: 4,
    name: 'Note Taker App',
    description: 'A beautiful weather dashboard with location-based forecasts and data visualization.',
    technologies: ['HTML', 'CSS', 'JavaScript', 'GitHub'],
    liveUrl: 'https://note-taker-app-g10.vercel.app/',
    githubUrl: 'https://github.com/Kin-Doung/Note-taker-app---G10',
    image: 'https://images.unsplash.com/photo-1484480974693-6ca0a78bcf5d?w=400&h=200&fit=crop',
    imageError: false
  },
  {
    id: 5,
    name: 'Web Design',
    description: 'Designed and developed a responsive static online shop website',
    technologies: ['HTML', 'CSS', 'SASS', 'GitHub'],
    liveUrl: 'https://www.figma.com/design/zs9ViHt3peNCXDVowff9xx/Project?node-id=51-2&p=f&t=mKGvLvVeE1jKsG1A-0',
    githubUrl: 'https://github.com/lealeacrazy/online-shop-B7',
    image: 'https://images.unsplash.com/photo-1467232004584-a241de8bcf5d?w=400&h=200&fit=crop',
    imageError: false
  },
])

// Smooth scrolling function
const scrollToSection = (sectionId) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}

const handleImageError = (event) => {
  // Hide the image and show fallback gradient background
  event.target.style.display = 'none'
}

const handleProjectImageError = (project) => {
  project.imageError = true
}

const handleProjectImageLoad = (project) => {
  project.imageError = false
}
</script>
