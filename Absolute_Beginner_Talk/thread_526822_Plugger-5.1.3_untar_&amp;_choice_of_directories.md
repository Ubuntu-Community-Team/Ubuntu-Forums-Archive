---
title: "Plugger-5.1.3 untar &amp; choice of directories"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-08-15
I want to listen to midi (type of sound cf. .mp3) files. I found software called Plugger that allows Firefox to associate file extensions with programs, call them and play/view them in firefox.

Very good. The homepage of Plugger: [http://fredrik.hubbe.net/plugger.html](http://fredrik.hubbe.net/plugger.html) has a download link. And reading the page I see the author suggests "If you want RPMs or DEBs, ask your distro maker." Well, I would be embarrassed to ask for so much, so I will ask for some help with this instead.

After downloading the program file: Plugger-5.1.3.tar.gz I have no idea of what to do with it for Ubuntu. I tried googling: ubuntu plugger as keywords, but that wasn't really helpful. I know there is a tar/untar command and looked at the manual, but don't know which directory to move the compressed file to before "opening" it.

Here are the authors instructions:

[B]   1.  Download and untar the archive.
   2. Change directory into the Plugger directory.
   3. Run ./configure
   4. Run make
   5. If you have root access, do 'make install' as root. Otherwise, do 'make localinstall'.
   6. done! [/B]

Does that mean that untar will create a directory "Plugger"? Do I have to create it manually? In what place / or /usr or /usr/lib et cetera.

Is this enough . . . tar -zxf file.tar.gz  or does it need some more letters? (I'm surprised I can't find a one or two page 'how-to' on tar)

Do I have to change the ownership of both the *.tar.gz or just the extracted file?

I see from some posts at these forums, that you need gcc and maybe other programs. How do I know before I install Plugger what is needed. What about dependencies too? Would Aptitude handle this better? That is: sudo aptitude install plugger?

I don't want to harm my happily running system just for midi files. I'm not sure I've covered all the contingencies I wanted to in this post, but it's a running start.

---

### Post by RAV TUX on 2007-11-29
> **Mark_in_Hollywood said:**
> I want to listen to midi (type of sound cf. .mp3) files. I found software called Plugger that allows Firefox to associate file extensions with programs, call them and play/view them in firefox.

Very good. The homepage of Plugger: [http://fredrik.hubbe.net/plugger.html](http://fredrik.hubbe.net/plugger.html) has a download link. And reading the page I see the author suggests "If you want RPMs or DEBs, ask your distro maker." Well, I would be embarrassed to ask for so much, so I will ask for some help with this instead.

After downloading the program file: Plugger-5.1.3.tar.gz I have no idea of what to do with it for Ubuntu. I tried googling: ubuntu plugger as keywords, but that wasn't really helpful. I know there is a tar/untar command and looked at the manual, but don't know which directory to move the compressed file to before "opening" it.

Here are the authors instructions:

[B]   1.  Download and untar the archive.
   2. Change directory into the Plugger directory.
   3. Run ./configure
   4. Run make
   5. If you have root access, do 'make install' as root. Otherwise, do 'make localinstall'.
   6. done! [/B]

Does that mean that untar will create a directory "Plugger"? Do I have to create it manually? In what place / or /usr or /usr/lib et cetera.

Is this enough . . . tar -zxf file.tar.gz  or does it need some more letters? (I'm surprised I can't find a one or two page 'how-to' on tar)

Do I have to change the ownership of both the *.tar.gz or just the extracted file?

I see from some posts at these forums, that you need gcc and maybe other programs. How do I know before I install Plugger what is needed. What about dependencies too? Would Aptitude handle this better? That is: sudo aptitude install plugger?

I don't want to harm my happily running system just for midi files. I'm not sure I've covered all the contingencies I wanted to in this post, but it's a running start.

This may help: in the Gutsy package search it is called mozplugger.

so you can install it by opening your terminal and typing(or copy and paste):

```
sudo apt-get install mozplugger
```or simply type(or copy and paste) this in your Firefox address field:

```
apt:mozplugger
```You can find more helpful information at the following:

[http://www.linuxmanpages.com/man7/mozplugger.7.php](http://www.linuxmanpages.com/man7/mozplugger.7.php)

[http://mozplugger.mozdev.org/](http://mozplugger.mozdev.org/)

---

