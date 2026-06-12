---
title: "compounded installation problems from a linux-ubuntu beginner"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by zmr on 2006-12-10
I recently have been attempting to install uim and m17nlib packages for the purpose of being able to input Asian fonts. These packages are perhaps the most single important programs/libraries for my computer given the work that I do. Thus even before I had ubuntu completely installed, I sought out the files online from the relevant websites and downloaded them as tar.gz files. Once ubuntu was running, I then proceeded to extract, compile and install them-- just as the instructions on the websites said to do. Later I realized that installing packages is best done on through apt-get or synaptic. Because I had not gotten the compiled source files working very well, I thought I would uninstall them and then start afresh by letting synaptic do all of the installation. Somewhere along the line things have gone wrong and although UIM  and m17nlib are installed via synaptic, UIM is not recognizing the m17nlib files-- presumably because, as one of the UIM experts speculated in an email (without my telling him any of the above), there's a version mismatch between the m17n-lib and m17n-db files I installed. If this is correct, is there an easy solution to cleaning out all of the uim and m17n files and starting the whole process anew? 

In windows, you could revert back to a previous restore point using system restore and all is better again. Is there anything analogous in ubuntu-linux? I would not mind too much if "the easy way" to solving this problem entailed losing other programs and configurations I have set-up since beginning on ubuntu (although it would be nice if it didn't. Also, re-installing ubuntu itself is not a very appealing either...)

anyways, i am a bit confused. Is there any clear guidance out there??! thanks

---

### Post by daou on 2006-12-10
You probably used a command such as "make" or "make install" to compile from source.

Check if you are able to run "make uninstall" instead. If it complains about something, you probably have to remove the installed files manually.

---

