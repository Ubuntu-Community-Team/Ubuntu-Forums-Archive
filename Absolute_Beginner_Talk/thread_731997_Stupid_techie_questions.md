---
title: "Stupid techie questions"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by Mulenmar on 2008-03-22
I want to install a game (Tux Racer), and I need to know if Ubuntu 7.1 already has these packages, or if I need to download them separately:

-  An implementation of the OpenGL API version 1.1 or greater 
- The GLUT library, version 3.7 beta or greater. . 
- Tcl Version 8.0 or greater. 
- (Optional) Simple DirectMedia Layer (SDL) Version 1.1.1 or greater. This is required for joystick support. 
- (Optional) SDL_mixer Version 1.0 or greater. This is required for sound and music support. 


(If you haven't figured it out, I know NOTHING about the workings of Linux.)

Hope you folks can help! :popcorn:

---

### Post by maddog39 on 2008-03-22
Yes, well ubuntu has this game in the repository (synaptic/apt) already but TuxRacer is an old game and hasnt been updated in a very long time. So a new project called Planet Penguin Racer was started to continue its development. So if you go to System > Administration > Synaptic Package Manager and you click on Search and search for planetpenguin-racer and select the packages planetpenguin-racer and planetpenguin-racer-extras, then click Apply to install them. Or if you dont want to do all that you can simply run this command in a terminal:
```

sudo apt-get install planetpenguin-racer planetpenguin-racer-extras

```

---

### Post by Mulenmar on 2008-03-22
Oh. Thanks! (*feels REALLY noobish*)

---

