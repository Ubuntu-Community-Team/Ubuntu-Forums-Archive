---
title: "[SOLVED] Apply Fluxbox Theme?"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Deadmode on 2008-01-06
I just got Fluxbox running with Ubuntu, but I'm kind of unclear what I need to do to apply a theme that I download.  Does anyone know?

---

### Post by mattator on 2008-01-06
You have tocopy the folder or file downloaded in ~/.fluxbox/styles.
Then you just have to choose it in your menu via :
Fluxbox menu -> User Style -> name_of_my_style
If you want your skint to be considered as a global oneyou have to put your skin into /usr/share/fluxbox/styles/

Good luck

---

### Post by Niniel on 2008-01-06
Not sure. I just tried it myself, but it's not right. I expected something like BBWin, but I don't have a root menu. How did you do it?

---

### Post by rjmdomingo2003 on 2008-01-06
> **Niniel said:**
> Not sure. I just tried it myself, but it's not right. I expected something like BBWin, but I don't have a root menu. How did you do it?
Here's a good tute: [http://ubuntuforums.org/showthread.php?t=371144&highlight=fluxbox+menu](http://ubuntuforums.org/showthread.php?t=371144&highlight=fluxbox+menu)

---

### Post by RedSquirrel on 2008-01-06
> **Deadmode said:**
> I just got Fluxbox running with Ubuntu, but I'm kind of unclear what I need to do to apply a theme that I download.  Does anyone know?

Most themes need to be extracted.

If the theme's filename ends in .tar.gz, run (in a terminal):

```
tar xzf theme-name -C ~/.fluxbox/styles
```If the theme's filename ends in .tar.bz2, run:

```
tar xjf theme-name -C ~/.fluxbox/styles
```(for more information on tar, see its manpage, 'man tar')

If you don't like the terminal, you can use whatever you like to extract the files, as long as they end up in the ~/.fluxbox/styles directory. Then the theme will appear in your menu, as mentioned above.

---

### Post by Deadmode on 2008-01-07
Thank you for replies.  But this is what I got when I entered what Redsquirrel told me to.

charles@server:~$ sudo tar xjf seer-o_influx.tar.bz2 -C ~/.fluxbox/styles
tar: /home/charles/.fluxbox/styles: Cannot chdir: No such file or directory
tar: Error is not recoverable: exiting now
charles@server:~$ cd /.fluxbox
-bash: cd: /.fluxbox: No such file or directory

Did I install fluxbox wrong?  It seems to be up and working. The fluxbox folder exists in /usr/share/fluxbox 
I have a feeling I've done something very wrong.  :-\

---

### Post by p_quarles on 2008-01-07
Typing```
cd /.fluxbox
```
looks for a directory named .fluxbox in the root filesystem. Did you actually type ~/.fluxbox? 

Anyway, if you really don't have a fluxbox directory in your /home, it'll still be easy to make one.

---

### Post by RedSquirrel on 2008-01-07
> **Deadmode said:**
> Thank you for replies.  But this is what I got when I entered what Redsquirrel told me to.

charles@server:~$ sudo tar xjf seer-o_influx.tar.bz2 -C ~/.fluxbox/styles
tar: /home/charles/.fluxbox/styles: Cannot chdir: No such file or directory
tar: Error is not recoverable: exiting now
charles@server:~$ cd /.fluxbox
-bash: cd: /.fluxbox: No such file or directory

Did I install fluxbox wrong?  It seems to be up and working. The fluxbox folder exists in /usr/share/fluxbox 
I have a feeling I've done something very wrong.  :-\

You don't need to use sudo.

Note that ~ means the same thing as /home/charles.

So, you would need to try

```
cd ~/.fluxbox
```not

```
cd /.fluxbox
```How are you starting fluxbox?

If you are starting it from the command line (by running 'startx'), you should have 

```
exec startfluxbox
```

at the bottom of your ~/.xinitrc file. The startfluxbox script creates the ~/.fluxbox directory and its contents (including the "styles" directory) the first time it is run.

---

### Post by bodhi.zazen on 2008-01-07
You may need to make the directory :

mkdir ~/.fluxbox/styles

---

### Post by Deadmode on 2008-01-08
> **RedSquirrel said:**
> You don't need to use sudo.

Note that ~ means the same thing as /home/charles.

So, you would need to try

```
cd ~/.fluxbox
```not

```
cd /.fluxbox
```How are you starting fluxbox?

If you are starting it from the command line (by running 'startx'), you should have 

```
exec startfluxbox
```

at the bottom of your ~/.xinitrc file. The startfluxbox script creates the ~/.fluxbox directory and its contents (including the "styles" directory) the first time it is run.

lol I'm not quite sure how I am starting fluxbox.  I set it up around 4 am and I had no idea what I was doing.  I'm going to retrace my steps and probably attempt to install and configure it properly.  Thank you for your responses :)

---

