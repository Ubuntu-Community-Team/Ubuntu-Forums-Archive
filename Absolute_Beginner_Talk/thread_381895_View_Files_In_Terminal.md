---
title: "View Files In Terminal"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by nhandler on 2007-03-11
I have had a few incidences where I have not had access to a gui, but I did have access to a TTY terminal. I know from a terminal that I can use cat, less, or more to view the contents of a text file. However, .doc files are encrypted in some fashion, so those commands don't work. Is there a way to view .doc files from the terminal? Or maybe there is a terminal command to copy the text from a .doc file to a plain text file. Along the same lines, I know there are ways to turn an image into a text file. It uses colored letters to show the image. Since the terminal can show colored text, is there a way to convert an image to a colored text file (maybe html?) and show it through the terminal?

The reason I'm asking this is to ensure that I always have access to my files, even when I can't get to a gui.

---

### Post by aysiu on 2007-03-11
I think your best bet is to have a live CD (the Desktop CD) handy. That way if your X ever gets screwed up, you can boot the Desktop CD and have a GUI. Better yet, get a Knoppix CD.

Still, if you're using Feisty Fawn (as your profile indicates), you should have "bullet-proof-x."
[https://blueprints.launchpad.net/ubuntu/+spec/bullet-proof-x](https://blueprints.launchpad.net/ubuntu/+spec/bullet-proof-x)

---

### Post by raja on 2007-03-11
Antiword is what you want to view .doc files in the terminal. It is available in the repositories. There is also a plugin to access abiword from the commandline. You can then call Abiword to convert the .doc to .txt file and then view it.

---

### Post by nhandler on 2007-03-11
Antiword works great for .doc files. Is there a way to convert image files to colored letters? I think gimp supports saving them that way. Is there a way to use gimp features from the terminal? Or maybe image magick?

---

