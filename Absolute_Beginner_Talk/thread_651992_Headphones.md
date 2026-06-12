---
title: "Headphones?"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by jhmaccuish on 2007-12-28
Hi, I'm new to ubuntu and linux OSs in general. I installed Ubuntu 7.10 with a dual boot with windows on my laptop but don't have sound on my headphones in ubuntu although it works fine in windows. The mixer doesn't seem to recognise the headphone device as there is no option for headphones in the volume control. Windows tells me that the sound card is called realtek high definition audio (although the teminal returned 0 [Intel          ]: HDA-Intel - HDA Intel HDA Intel at 0xfc300000 irq 22). So i tried downloading the linux drivers from the realtek webpage (i tried both drivers 2.4 or 2.6 and RHEL 4 update 4) extracted the files using archive manager and tried to install them executing the code in ./install in the terminal. But I get the same problem with both that is it returns permission denied. I've been looking around and have seen some suggestions that this might be a problem of root privilege but not sure how to change this and run the install file dirrectly in the terminal. Can some one tell me how to do this or am I barking up completly the wrong tree?

---

### Post by adam.tropics on 2007-12-28
A good guide to installing manually from source [is here]("http://monkeyblog.org/ubuntu/installing/#installing_with_terminal"), though without meaning to suggest you've missed anything obvious, I have attached a picture....you may just want to check that headphone controls are set to be displayed. Open the volume controls, and check the preferences found in the edit menu. Also, from the file menu, check you are looking at the correct controls.

---

### Post by rune0077 on 2007-12-28
To run the installer from the terminal, you need to be in the directory where you have the program. Type "cd" followed by the path of the directory. Once there, type in the name of installer program, and it should run. To run it as root, type "sudo" before the name, then type your password when prompted for it.

---

