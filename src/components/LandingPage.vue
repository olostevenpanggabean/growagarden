<template>
  <div class="landing-container">
    <!-- Animated Background Elements -->
    <div class="bg-animations">
      <div class="particle" v-for="n in 20" :key="n" :style="getParticleStyle(n)"></div>
    </div>

    <!-- Floating Elements -->
    <div class="floating-elements">
      <div 
        v-for="(element, index) in floatingElements" 
        :key="index"
        class="floating-element"
        :style="{ 
          top: element.top, 
          left: element.left,
          animationDelay: element.delay 
        }"
      >
        {{ element.icon }}
      </div>
    </div>
    
    <div class="content-wrapper" :class="{ 'loaded': isLoaded }">
      <!-- Hero Section -->
      <div class="hero-section">
        <div class="logo-section">
          <div class="main-logo">🎮</div>
          <div class="logo-glow"></div>
        </div>
        
        <h1 class="main-title">
          <span class="title-main">Kwirawww STORE</span>
          <span class="highlight">Grow a Garden</span>
          <span class="subtitle">Divine & Legendary Collection</span>
        </h1>
        
        <p class="description">
          Koleksi pet terlengkap dengan harga terjangkau. Semua pet original dan aman!
          <br><strong>Chat Admin</strong> untuk informasi lebih lanjut.
        </p>

        <!-- Action Buttons -->
        <div class="button-group">
          <a 
            :href="whatsappLink" 
            target="_blank" 
            class="btn btn-primary"
            @click="trackClick('whatsapp')"
          >
            <span class="btn-icon"></span>
            <span class="btn-text">Chat WhatsApp</span>
            <div class="btn-effect"></div>
          </a>
          
          <a 
            :href="saweriaLink" 
            target="_blank" 
            class="btn btn-secondary"
            @click="trackClick('saweria')"
          >
            <span class="btn-icon"></span>
            <span class="btn-text">saweria</span>
            <div class="btn-effect"></div>
          </a>
        </div>
      </div>

      <!-- Pet Categories -->
      <div class="category-section">
        <h2 class="section-title">🔥 DIVINE PETS COLLECTION</h2>
        <div class="pets-grid">
          <div 
            v-for="(pet, index) in divinePets" 
            :key="index"
            class="pet-card"
            :style="{ animationDelay: `${0.1 + index * 0.1}s` }"
          >
            <div class="pet-rarity divine">DIVINE</div>
            <div class="pet-icon">{{ pet.icon }}</div>
            <div class="pet-name">{{ pet.name }}</div>
            <div class="pet-price">{{ pet.price }}</div>
          </div>
        </div>
      </div>

      <!-- Features Section -->
      <div class="features-section">
        <h3 class="section-title">Kenapa Memilih Kwirawww?</h3>
        <div class="features-grid">
          <div 
            v-for="(feature, index) in features" 
            :key="index"
            class="feature-card"
            :style="{ animationDelay: `${0.5 + index * 0.2}s` }"
          >
            <div class="feature-icon">{{ feature.icon }}</div>
            <div class="feature-title">{{ feature.title }}</div>
            <div class="feature-desc">{{ feature.desc }}</div>
          </div>
        </div>
      </div>

      <!-- Stats Section -->
      <div class="stats-section">
        <div class="stats-grid">
          <div class="stat-item">
            <div class="stat-number">500+</div>
            <div class="stat-label">Happy Customers</div>
          </div>
          <div class="stat-item">
            <div class="stat-number">24/7</div>
            <div class="stat-label">Fast Response</div>
          </div>
          <div class="stat-item">
            <div class="stat-number">100%</div>
            <div class="stat-label">Safe & Original</div>
          </div>
        </div>
      </div>

      <!-- CTA Section -->
      <div class="cta-section">
        <div class="cta-content">
          <h3 class="cta-title">Ready to Get Your Dream Pet?</h3>
          <p class="cta-desc">Contact us now and get special discount for first purchase!</p>
          <a 
            :href="whatsappLink" 
            target="_blank" 
            class="btn btn-cta"
            @click="trackClick('whatsapp-cta')"
          >
            <span class="btn-text">🚀 Order Now!</span>
            <div class="btn-pulse"></div>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'RobloxPetStore',
  data() {
    return {
      isLoaded: false,
      whatsappNumber: '6282385311215',
      saweriaUsername: 'Kwirawww',

      floatingElements: [
        { icon: '⚡', top: '15%', left: '10%', delay: '0s' },
        { icon: '💎', top: '25%', left: '85%', delay: '2s' },
        { icon: '🔥', top: '65%', left: '15%', delay: '4s' },
        { icon: '⭐', top: '70%', left: '80%', delay: '1s' },
        { icon: '🎯', top: '45%', left: '5%', delay: '3s' },
        { icon: '🏆', top: '35%', left: '90%', delay: '5s' },
      ],

      divinePets: [
        { icon: '🦊', name: 'Red Fox', price: '10K' },
        { icon: '🦝', name: 'Raccoon', price: '80K' },
        { icon: '🦖', name: 'T-Rex', price: '65K' },
        { icon: '🐙', name: 'Mimic Octopus', price: '40K' },
        { icon: '🜸', name: 'Dragonfly', price: '40K' },
        { icon: '🦋', name: 'Butterfly', price: '70K' },
        { icon: '🐝', name: 'Disco Bee', price: '70K' },
        { icon: '🦕', name: 'Spinosaurus', price: '70K' },
        { icon: '🐔', name: 'Zombie Chicken', price: '25K' },
        { icon: '🦉', name: 'Blood Owl', price: '20K' },
        { icon: '🐱', name: 'Moon Cat', price: '10K' },
        { icon: '🐉', name: 'Kitsune', price: 'Comming Soon' }
      ],

      features: [
        {
          icon: '⚡',
          title: 'Lightning Fast',
          desc: 'Proses Cepat Hanya 5 Menit!'
        },
        {
          icon: '🛡️',
          title: '100% Secure',
          desc: 'Sudah Terbukti dan Banyak Testimoni!'
        },
        {
          icon: '💰',
          title: 'Best Price',
          desc: 'Dijamin Murah!'
        },
        {
          icon: '🎁',
          title: 'Bonus Deal',
          desc: 'Dapatkan Bonus Shekles!'
        }
      ]
    }
  },

  computed: {
    whatsappLink() {
      const message = encodeURIComponent('Hi! I want to buy Divine pets from Roblox Grow a Garden. What\'s available?');
      return `https://wa.me/${this.whatsappNumber}?text=${message}`;
    },

    saweriaLink() {
      return `https://saweria.co/${this.saweriaUsername}`;
    }
  },

  mounted() {
    setTimeout(() => {
      this.isLoaded = true;
    }, 100);

    this.setupScrollAnimations();
  },

  methods: {
    trackClick(button) {
      console.log(`User clicked: ${button}`);
    },

    getParticleStyle(index) {
      return {
        left: Math.random() * 100 + '%',
        animationDelay: Math.random() * 10 + 's',
        animationDuration: (Math.random() * 10 + 15) + 's'
      };
    },

    setupScrollAnimations() {
      const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            entry.target.classList.add('animate-in');
          }
        });
      });

      this.$nextTick(() => {
        const elements = this.$el.querySelectorAll('.feature-card, .pet-card, .btn');
        elements.forEach(el => observer.observe(el));
      });
    }
  }
}
</script>


<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Roboto:wght@400;500;700&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.landing-container {
  min-height: 100vh;
  background: linear-gradient(135deg, 
    #0c0c0c 0%, 
    #1a1a2e 25%, 
    #16213e 50%, 
    #0f3460 75%, 
    #533a7b 100%
  );
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 20px;
  font-family: 'Roboto', sans-serif;
  overflow-x: hidden;
}

/* Animated Background */
.bg-animations {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 0;
}

.particle {
  position: absolute;
  width: 2px;
  height: 2px;
  background: rgba(255, 255, 255, 0.6);
  border-radius: 50%;
  animation: particleFloat 20s linear infinite;
}

@keyframes particleFloat {
  0% {
    transform: translateY(100vh) rotate(0deg);
    opacity: 0;
  }
  10% {
    opacity: 1;
  }
  90% {
    opacity: 1;
  }
  100% {
    transform: translateY(-100px) rotate(360deg);
    opacity: 0;
  }
}

/* Floating Elements */
.floating-elements {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 1;
}

.floating-element {
  position: absolute;
  font-size: 2rem;
  animation: floatElement 15s linear infinite;
  opacity: 0.2;
  color: #64ffda;
}

@keyframes floatElement {
  0% { transform: translateY(0px) rotate(0deg) scale(1); }
  25% { transform: translateY(-30px) rotate(90deg) scale(1.2); }
  50% { transform: translateY(20px) rotate(180deg) scale(0.8); }
  75% { transform: translateY(-25px) rotate(270deg) scale(1.1); }
  100% { transform: translateY(0px) rotate(360deg) scale(1); }
}

/* Main Content */
.content-wrapper {
  position: relative;
  z-index: 2;
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(15px);
  border-radius: 20px;
  padding: 40px 30px;
  border: 1px solid rgba(255, 255, 255, 0.1);
  box-shadow: 
    0 25px 45px rgba(0, 0, 0, 0.3),
    inset 0 1px 0 rgba(255, 255, 255, 0.1);
  max-width: 800px;
  width: 100%;
  opacity: 0;
  transform: translateY(50px) scale(0.9);
  transition: all 1s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}

.content-wrapper.loaded {
  opacity: 1;
  transform: translateY(0) scale(1);
}

/* Hero Section */
.hero-section {
  text-align: center;
  margin-bottom: 50px;
}

.logo-section {
  position: relative;
  margin-bottom: 30px;
}

.main-logo {
  font-size: 5rem;
  display: inline-block;
  animation: logoGlow 3s ease-in-out infinite;
  position: relative;
  z-index: 2;
}

.logo-glow {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 120px;
  height: 120px;
  background: radial-gradient(circle, rgba(100, 255, 218, 0.3), transparent);
  border-radius: 50%;
  animation: pulse 2s ease-in-out infinite;
}

@keyframes logoGlow {
  0%, 100% { 
    transform: scale(1);
    filter: drop-shadow(0 0 20px #64ffda);
  }
  50% { 
    transform: scale(1.05);
    filter: drop-shadow(0 0 30px #64ffda);
  }
}

@keyframes pulse {
  0%, 100% { transform: translate(-50%, -50%) scale(1); opacity: 0.7; }
  50% { transform: translate(-50%, -50%) scale(1.2); opacity: 0.3; }
}

.main-title {
  margin-bottom: 25px;
  line-height: 1.3;
}

.title-main {
  display: block;
  font-family: 'Orbitron', monospace;
  font-size: 2.2rem;
  font-weight: 900;
  color: #ffffff;
  text-shadow: 0 0 20px rgba(100, 255, 218, 0.5);
  margin-bottom: 10px;
  letter-spacing: 2px;
}

.highlight {
  display: block;
  font-family: 'Orbitron', monospace;
  font-size: 2rem;
  font-weight: 700;
  background: linear-gradient(45deg, #64ffda, #00bcd4, #2196f3, #3f51b5);
  background-size: 300% 300%;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  animation: gradientShift 4s ease infinite;
  margin-bottom: 8px;
}

.subtitle {
  display: block;
  font-size: 1.2rem;
  color: #b0bec5;
  font-weight: 500;
  text-shadow: 0 0 10px rgba(176, 190, 197, 0.3);
}

@keyframes gradientShift {
  0%, 100% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
}

.description {
  color: #e0e0e0;
  font-size: 1.1rem;
  margin-bottom: 40px;
  font-weight: 400;
  line-height: 1.6;
  max-width: 500px;
  margin-left: auto;
  margin-right: auto;
}

/* Buttons */
.button-group {
  display: flex;
  gap: 20px;
  justify-content: center;
  margin-bottom: 50px;
  flex-wrap: wrap;
}

.btn {
  padding: 16px 32px;
  border-radius: 8px;
  text-decoration: none;
  font-weight: 600;
  font-size: 1rem;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
  border: 1px solid transparent;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  text-align: center;
  min-width: 180px;
}

.btn-primary {
  background: linear-gradient(45deg, #00c851, #007e33);
  color: white;
  border-color: #00c851;
  box-shadow: 0 4px 15px rgba(0, 200, 81, 0.3);
}

.btn-secondary {
  background: linear-gradient(45deg, #ff5722, #bf360c);
  color: white;
  border-color: #ff5722;
  box-shadow: 0 4px 15px rgba(255, 87, 34, 0.3);
}

.btn-cta {
  background: linear-gradient(45deg, #2196f3, #0d47a1);
  color: white;
  font-size: 1.1rem;
  padding: 18px 36px;
  border-color: #2196f3;
  box-shadow: 0 4px 15px rgba(33, 150, 243, 0.4);
}

.btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
}

.btn-effect {
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
  transition: left 0.5s;
}

.btn:hover .btn-effect {
  left: 100%;
}

/* Pet Categories */
.category-section {
  margin-bottom: 50px;
}

.section-title {
  font-family: 'Orbitron', monospace;
  font-size: 1.8rem;
  font-weight: 700;
  color: #64ffda;
  text-align: center;
  margin-bottom: 30px;
  text-shadow: 0 0 15px rgba(100, 255, 218, 0.5);
}

.pets-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 20px;
  margin-bottom: 30px;
}

.pet-card {
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
  border-radius: 15px;
  padding: 20px;
  text-align: center;
  border: 1px solid rgba(255, 255, 255, 0.1);
  transition: all 0.3s ease;
  opacity: 0;
  transform: translateY(30px);
  animation: fadeInUp 0.6s ease forwards;
  position: relative;
  overflow: hidden;
}

.pet-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(100, 255, 218, 0.1), transparent);
  transition: left 0.5s;
}

.pet-card:hover::before {
  left: 100%;
}

.pet-card:hover {
  transform: translateY(-5px) scale(1.02);
  box-shadow: 0 10px 30px rgba(100, 255, 218, 0.2);
  border-color: rgba(100, 255, 218, 0.3);
}

.pet-rarity {
  position: absolute;
  top: 10px;
  right: 10px;
  padding: 4px 8px;
  border-radius: 12px;
  font-size: 0.7rem;
  font-weight: 700;
  text-transform: uppercase;
}

.pet-rarity.divine {
  background: linear-gradient(45deg, #ff9800, #f57c00);
  color: white;
  box-shadow: 0 0 10px rgba(255, 152, 0, 0.5);
}

.pet-icon {
  font-size: 3rem;
  margin-bottom: 15px;
  display: block;
  animation: petFloat 3s ease-in-out infinite;
}

.pet-name {
  font-weight: 600;
  color: #ffffff;
  margin-bottom: 8px;
  font-size: 1.1rem;
}

.pet-price {
  font-size: 1.2rem;
  font-weight: 700;
  color: #64ffda;
  text-shadow: 0 0 10px rgba(100, 255, 218, 0.5);
}

@keyframes petFloat {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-8px); }
}

/* Features Section */
.features-section {
  margin-bottom: 50px;
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
  gap: 20px;
}

.feature-card {
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
  border-radius: 15px;
  padding: 25px 20px;
  text-align: center;
  border: 1px solid rgba(255, 255, 255, 0.1);
  transition: all 0.3s ease;
  opacity: 0;
  transform: translateY(30px);
  animation: fadeInUp 0.6s ease forwards;
}

.feature-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
}

.feature-icon {
  font-size: 2.5rem;
  margin-bottom: 15px;
  display: block;
}

.feature-title {
  font-weight: 700;
  color: #ffffff;
  margin-bottom: 8px;
  font-size: 1.1rem;
}

.feature-desc {
  font-size: 0.9rem;
  color: #b0bec5;
  line-height: 1.4;
}

/* Stats Section */
.stats-section {
  margin-bottom: 50px;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 30px;
  text-align: center;
}

.stat-item {
  color: white;
}

.stat-number {
  font-family: 'Orbitron', monospace;
  font-size: 2.5rem;
  font-weight: 900;
  color: #64ffda;
  text-shadow: 0 0 15px rgba(100, 255, 218, 0.5);
  margin-bottom: 8px;
}

.stat-label {
  font-size: 0.9rem;
  color: #b0bec5;
  font-weight: 500;
}

/* CTA Section */
.cta-section {
  background: linear-gradient(45deg, rgba(100, 255, 218, 0.1), rgba(33, 150, 243, 0.1));
  border-radius: 20px;
  padding: 40px 30px;
  text-align: center;
  border: 1px solid rgba(100, 255, 218, 0.2);
  position: relative;
  overflow: hidden;
}

.cta-section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(45deg, rgba(100, 255, 218, 0.05), rgba(33, 150, 243, 0.05));
  animation: cta-glow 3s ease-in-out infinite;
}

@keyframes cta-glow {
  0%, 100% { opacity: 0.5; }
  50% { opacity: 1; }
}

.cta-content {
  position: relative;
  z-index: 1;
}

.cta-title {
  font-family: 'Orbitron', monospace;
  font-size: 1.8rem;
  font-weight: 700;
  color: #64ffda;
  margin-bottom: 15px;
  text-shadow: 0 0 15px rgba(100, 255, 218, 0.5);
}

.cta-desc {
  color: #e0e0e0;
  font-weight: 500;
  margin-bottom: 30px;
  line-height: 1.5;
}

.btn-pulse {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  border-radius: 8px;
  background: rgba(33, 150, 243, 0.3);
  animation: btn-pulse 2s infinite;
}

@keyframes btn-pulse {
  0% { transform: scale(1); opacity: 1; }
  100% { transform: scale(1.05); opacity: 0; }
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Responsive Design */
@media (max-width: 768px) {
  .content-wrapper {
    padding: 30px 20px;
    margin: 10px;
  }
  
  .main-logo {
    font-size: 4rem;
  }
  
  .title-main {
    font-size: 1.8rem;
  }
  
  .highlight {
    font-size: 1.6rem;
  }
  
  .button-group {
    flex-direction: column;
    align-items: center;
  }
  
  .pets-grid {
    grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
    gap: 15px;
  }
  
  .features-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 15px;
  }
  
  .stats-grid {
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
  }
  
  .stat-number {
    font-size: 2rem;
  }
}

@media (max-width: 480px) {
  .content-wrapper {
    padding: 25px 15px;
  }
  
  .pets-grid {
    grid-template-columns: 1fr 1fr;
  }
  
  .features-grid {
    grid-template-columns: 1fr;
  }
  
  .btn {
    min-width: 150px;
    padding: 14px 24px;
  }
}
</style>