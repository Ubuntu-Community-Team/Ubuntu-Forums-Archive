---
title: "Java - install help..."
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by wakaimono on 2006-09-08
Ok, I downloaded jre-1_5_0_06-linux-i586.bin from the Java website. Made it executable, it did it's thing, these are the configure instructions, and as linux newbie don't understand them.

 Mozilla 1.4 and later

   1. Go to the plugins sub-directory under the Mozilla installation directory
      cd <Mozilla installation directory>/plugins
   2. In the current directory, create a symbolic link to the JRE ns7/libjavaplugin_oji.so file Type:
      ln -s <JRE installation directory>/plugin/i386/ns7/libjavaplugin_oji.so

      Example:
          * If Mozilla is installed in this directory:
            /usr/lib/mozilla-1.4/
          * and if the JRE is installed at this directory:
            /usr/java/jre1.5.0
          * Then type at the terminal to go to the browser plug-in directory:
            cd /usr/lib/mozilla-1.4/plugins
          * Enter the following command to create a symbolic link to the Java Plug-in for the Mozilla browser.
            ln -s /usr/java/jre1.5.0/plugin/i386/ns7
            /libjavaplugin_oji.so .
   3. Start Mozilla browser or restart it if it is already running. Note that if you have other Mozilla components (ie: Messenger, Composer, etc) running, you will need to restart them as well.
   4. Go to Edit > Preferences. Under Advanced category > Select Enable Java

---

### Post by howardepgco on 2006-09-08
I had trouble getting java too,but someone from this forum told me about Automatix.I think it is a repository of programs you can install to Ubuntu.Just search here for Automatix.There are some great how too's from some people way smarter than me.For me it just installed automatically. Anyway good luck.

---

### Post by wakaimono on 2006-09-08
Thanks

After a bit of reading the other threads, I found out how to get to root in terminal mode. Made all the other stuff easier to do.

---

### Post by DougieFresh4U on 2006-09-08
I'm new myself but I have learned a few tricks. There wre two dif. java's i had to install and both were in add/remove-Sun java 5 & java 1.4 and also Macroflash was inthere as well for those that need!! Hope this was helpfull. Peace!:evil:

---

