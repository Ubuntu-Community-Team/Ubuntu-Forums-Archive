---
title: "Installing from a source code"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Ross86 on 2007-03-12
Hi everyone,
I've recently downloaded Ubuntu, but as a total amateur I'm having a few problems installing a program. 
I'm trying to install ABC torrent. I've downloaded the source code, and done the 'Extract here' thing which has given me a folder entitled "ABC-Linux-V.2.4.3-alpha.tar.gz" on my desktop.
I've tried reading walk-through guides etc but I'm completely stuck, this is as far as I've got.
Would someone (preferably in good, simple plain english!) be able to give an idiots guide of what to to next. Don't take that I know anything for granted. I am a complete beginner.

This would be much appreciated. And I will love you. :)

---

### Post by taurus on 2007-03-12
Section 4.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Ek0nomik on 2007-03-12
Try this:

```
cd DIRECTORY.OF.ABC
dir
gedit README
```

There is usually a readme file included in every source directory, so you should be able to read that and it will give you instructions.

I hope that helps!

Cheers!

---

### Post by visik7 on 2007-03-12
there are tons of torrent client under ubuntu just pick one instead of compiling one by yourself that is  bad supported
ktorrent under kde , azureus, deludge under gnome just to quoting a bunch

---

### Post by Ross86 on 2007-03-12
visik7, I've tried using a few of the ones that you named, and I agree that this would be a hell of a lot simpler. But when I start downloading a torrent it gets so far (with a really slow download speed) and then says 'stalled'. I've tried a few different torrent files, but it seems to happen on all of them.

I've always used ABC on Windows and have never had any problems so I figured this would be the best one to use. 

Ek0nomik, I presume you mean to type that stuff in the terminal screen? Because when I type what you said I just seem to get an error.

---

### Post by Ross86 on 2007-03-12
If it's any help to anyone, these are the error messages that I get.

tar: ABC.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by Ek0nomik on 2007-03-12
> **Ross86 said:**
> If it's any help to anyone, these are the error messages that I get.

tar: ABC.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Post your exact terminal output and I should be able to help more.

This is what you want to do (yes, I mean type this in the Terminal):

```
cd directory
```

cd will move you into the directory you extracted on your Desktop.  So, for an example you may type this: cd Desktop/ABC.Directory.Whatever.This.Is.Called

Now type "dir", and it will list the contents inside that directory.

There *should* be a readme file.  You can open that by typing "gedit whatever.the.file.name.is".

Let me know how it goes, and post me some output and I will try to walk you through it.

Cheers!

---

### Post by Ross86 on 2007-03-12
Anyone? :confused:

---

### Post by Ek0nomik on 2007-03-12
> **Ross86 said:**
> Anyone? :confused:

Look up.  No, not at the ceiling.  One post above yours.  ;)

---

### Post by Ross86 on 2007-03-13
Ok, so I got into the directory, and read the readme file (which just directed me to their website and was of no help whatsoever!)

Now according to a guide I've got I now enter "./configure" in the terminal and then "make". Is this right, because as soon as I enter ./configure and then enter I get a "No such file or directory" error.

Apparently after this I type "sudo make install" and then that's it.

Sounds too good to be true! And anyway I haven't got that far yet!

---

### Post by louieb on 2007-03-13
Have you installed build-essential?

---

### Post by Ross86 on 2007-03-13
I have Louie.

---

### Post by Ross86 on 2007-03-13
I'm also having problems in that I've installed the Debian menu but can't seem to access it, and have also downloaded BitTornado and that seems to have disappeared also.

My main objective though is to get ABC torrent working!

Maybe someone could try it from start to finish on their system and let me know how they did it? Or is that too cheeky? ;)

---

### Post by Ross86 on 2007-03-13
Anyone? I'm really having no luck with this so far. :confused:

---

