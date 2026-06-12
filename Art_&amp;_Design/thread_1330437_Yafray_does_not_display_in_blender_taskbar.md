---
title: "Yafray does not display in blender taskbar"
date: 2009-11-18
forum: Art &amp; Design
---

### Post by dreamsR4living on 2009-11-18
Yesterday I installed Yafray from the repositories to render my scenes in Blender. 

The problem is that I cannot find any Yafray button or setting inside Blender after installation. Several websites tell that Yafray should display in the Render menu in Blenders taskbar, or there should be an option onder the big Render button in the buttons window.

I am using Ubuntu 9.10 i368 and Blender 2.49a. Does anyone have any idea what I can do to render with Yafray?

I know I can also render files with Yafray from terminal, but that is not the way I like to go.

---

### Post by svenni on 2009-11-20
I have the same problem on two different computers. One with a fresh Karmic install, and one with an upgrade.

I had the same problem in Intrepid when upgrading to Blender 2.49. I think the issue is that Blender 2.49 is compiled with the Python 2.5 libraries when installing from Ubuntu's repositories. Yafray seems to need Python 2.6.

---

### Post by TyrantWave on 2009-11-23
Yafray has been discontinued.

To use the newer yaf*a*ray renderer, make sure you installed Blender with the 2.6 python libraries, then you can export to Yafaray from the Render menu on the top.

---

### Post by gabrielaca on 2009-11-27
have you tried this? in the 3d buttons pane, click scene, or F10,there is a big RENDER button, beneath it there is a pull down menu (little arrow pointing down) click it and choose Yafray; i bealive _Yafaray_ (the newest incarnation) works the same way althoug it needs python 2.6, hope this helps.

one more thing, why not ask in Blendernation forums too?

---

### Post by TyrantWave on 2009-11-28
> **gabrielaca said:**
> have you tried this? in the 3d buttons pane, click scene, or F10,there is a big RENDER button, beneath it there is a pull down menu (little arrow pointing down) click it and choose Yafray; i bealive _Yafaray_ (the newest incarnation) works the same way althoug it needs python 2.6, hope this helps.

one more thing, why not ask in Blendernation forums too?

Nope, the new Yafaray only works via the export render (Still easy to use).
The Yafray button is gone, as it was discontiuned from 2.47 onwards IIRC.

---

### Post by dreamsR4living on 2009-12-01
> To use the newer yafaray renderer, make sure you installed Blender with the 2.6 python libraries, then you can export to Yafaray from the Render menu on the top.

I have installed both the most recent Yafaray and Blender from the project websites. It is working somehow, but when I try to save my Yafaray render, Blender crashes.

The current Blender and Yafray packages in Ubuntu are a mismatch. I think this could be considered an ubuntu bug. I am thinking about reporting this issue on launchpad.

---

