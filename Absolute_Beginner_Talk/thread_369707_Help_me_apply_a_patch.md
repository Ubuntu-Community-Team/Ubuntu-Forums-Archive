---
title: "Help me apply a patch?"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by squig on 2007-02-24
Below are the directions on [http://sourceforge.net/project/shownotes.php?release_id=481157&group_id=149981](http://sourceforge.net/project/shownotes.php?release_id=481157&group_id=149981)

I've downloaded the patch, and moved it to /usr/share/doc/hplip-1.7.1

What do I do from here? When I enter  
patch -p1 < 

 I get
bash: syntax error near unexpected token `newline'


How to apply the patch:
cd hplip-1.7.1
patch -p1 < 
hplip-1.7.1-1.patch
./configure --prefix=/usr
make clean
make
make install

Any help greatly appreciated. Thanks for your patience.
A

---

### Post by yabbadabbadont on 2007-02-24
patch -p1 < hplip-1.7.1-1.patch

It should be on one line.  It is saying, patch using the file hplip-1.7.1-1.patch

---

### Post by squig on 2007-02-24
Now it asks:

File to patch:


What do I put?

---

### Post by squig on 2007-02-24
amy@amy-laptop:/usr/share/doc/hplip-1.7.1$ patch -p1 < hplip-1.7.1-1.patch
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -uNr hplip-1.7.1_old/prnt/hpijs/dj3320.cpp hplip-1.7.1_new/prnt/hpijs/dj3320.cpp
|--- hplip-1.7.1_old/prnt/hpijs/dj3320.cpp      2007-01-24 15:42:03.000000000 -0800
|+++ hplip-1.7.1_new/prnt/hpijs/dj3320.cpp      2007-01-31 13:33:42.000000000 -0800
--------------------------
File to patch: 

This is what I get. I'm not sure what file I should be directing it to. Is it one of the files in the list above?

---

### Post by yabbadabbadont on 2007-02-24
Try running the patch command from the /usr/share/doc directory.  Like this:

amy@amy-laptop:/usr/share/doc/$ patch -p1 < hplip-1.7.1/hplip-1.7.1-1.patch

---

### Post by yabbadabbadont on 2007-02-24
I must apologize, I've just gone through and read the information from your sourceforge link.  The patch is to be applied to the source code of the hplip program which you were supposed to download and extract somewhere.  Then you are expected to recompile the program.  Were you expecting the patch to change the hplip program that is installed from the Ubuntu repostitories?

---

### Post by squig on 2007-02-24
Yes, I was. I guess the real problem is that I don't understand yet how it works... how to actually apply the patch. I apologize.

---

### Post by yabbadabbadont on 2007-02-24
> **squig said:**
> Yes, I was. I guess the real problem is that I don't understand yet how it works... how to actually apply the patch. I apologize.

No need to apologize.  It is a common mistake.  Unlike a windows patch, which pretty much replaces a binary program with a newer version, this patch is just a text file that contains the differences between other text files that are part of the sourcecode for the hplip program.  Just in case you don't already know, sourcecode is the text form of the computer instructions that make up the binary program, hplip.  This text must be compiled, changed from text into machine language, in order to produce the binary program that you actually run.  Unless the patch provides something you really can't live without, (i.e. your printer won't work without it), it is probably more trouble than it is worth to try to patch and compile the hplip program.

I hope I didn't just make things more confusing.  :)

---

### Post by squig on 2007-02-24
Yes, thanks. This does help a lot. The problem I'm having with the printer is pretty annoying. The printer basically freezes after every print job, and I have to restart the printer, restart cups, restart hplip, and delete all print jobs so that it will print again. This patch, from what I can tell, fixes exatly the problem I'm having. So I guess I would like to try to do it. 

I understand about source code. I know HTML, at least, so I'm not completely dumb to the concept. I think that I need to uninstall hplip, download 1.7.1 again, apply the patch to some spot in some part of the hplip directory, and then "configure." I've done both the manual install and the installer install of hplip before, trying to fix this, so I think I'm up to the task, I just don't know exactly how to do it.

~A

---

### Post by squig on 2007-02-24
So how do I know where I need to put the code that's in the patch? Does the text before the } in the patch text (pasted below) tell me where to put it? 

diff -uNr hplip-1.7.1_old/prnt/hpijs/dj3320.cpp hplip-1.7.1_new/prnt/hpijs/dj3320.cpp
--- hplip-1.7.1_old/prnt/hpijs/dj3320.cpp	2007-01-24 15:42:03.000000000 -0800
+++ hplip-1.7.1_new/prnt/hpijs/dj3320.cpp	2007-01-31 13:33:42.000000000 -0800
@@ -3066,7 +3066,7 @@
     }
 
     // Send Sync packet
-    err = pPrinterXBow->Send (pbySync, (DWORD) sizeof (pbySync));
+    err = pPrinterXBow->Send (pbySync, SYNCSIZE);
     if(err)
     {
         return err;

---

### Post by yabbadabbadont on 2007-02-24
Just extract the source code in any subdirectory of your home directory.  (I use ~/code personally)  When the code is extracted, it will probably create a new directory in the ~/code directory, let's assume it is called hplip-1.7.1.  Put the patch in the ~/code directory then run the "patch -p1 < hplip-1.7.1-1.patch" command from ~/code.  The "-p1" tells patch to ignore the first directory listed in the patch so it should work fine.  Assuming that there are no errors, you should then be able to change directory into ~/code/hplip-1.7.1 and then follow the instructions for configure/make/... that the site lists for building and installing the program.

---

### Post by confused57 on 2007-02-24
> **squig said:**
> So how do I know where I need to put the code that's in the patch? Does the text before the } in the patch text (pasted below) tell me where to put it? 

diff -uNr hplip-1.7.1_old/prnt/hpijs/dj3320.cpp hplip-1.7.1_new/prnt/hpijs/dj3320.cpp
--- hplip-1.7.1_old/prnt/hpijs/dj3320.cpp	2007-01-24 15:42:03.000000000 -0800
+++ hplip-1.7.1_new/prnt/hpijs/dj3320.cpp	2007-01-31 13:33:42.000000000 -0800
@@ -3066,7 +3066,7 @@
     }
 
     // Send Sync packet
-    err = pPrinterXBow->Send (pbySync, (DWORD) sizeof (pbySync));
+    err = pPrinterXBow->Send (pbySync, SYNCSIZE);
     if(err)
     {
         return err;

I'm no expert, but you might try:
```
sudo gedit hplip-1.7.1-1.patch
```

Then copy & paste the above into the file, then make sure the text file is in the source directory of your extracted file.  Actually, it's easier to select "Save As" & move to your source directory.

Yabbadabbadont knows much more than I about compiling...what I suggested may not work.

---

### Post by squig on 2007-02-24
created ~/code
dowloaded and extracted hplil-1.7.1.tar.gz into ~/code
moved hplip-1.7.1.patch to ~/code
ran the patch command


I am still getting the same error. 


amy@amy-laptop:~/code$ patch -p1 < hplip-1.7.1-1.patch
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -uNr hplip-1.7.1_old/prnt/hpijs/dj3320.cpp hplip-1.7.1_new/prnt/hpijs/dj3320.cpp
|--- hplip-1.7.1_old/prnt/hpijs/dj3320.cpp      2007-01-24 15:42:03.000000000 -0800
|+++ hplip-1.7.1_new/prnt/hpijs/dj3320.cpp      2007-01-31 13:33:42.000000000 -0800
--------------------------
File to patch:


I'm sorry. I'm doing my best, but I just don't understand quite enough, I guess. which file is the file to patch? Thanks for the help so far, by the way. I am learning a lot.

---

### Post by confused57 on 2007-02-24
Are you using -p(one) or -p(L)?  I think it's -p(one).

---

### Post by squig on 2007-02-24
Yah, I am using -p(one)

Should I try -p(letter L) ?

---

### Post by confused57 on 2007-02-24
> **squig said:**
> Yah, I am using -p(one)

Should I try -p(letter L) ?

I think I see your problem you need to be in your actual source directory that was extracted & make sure your patch file is also in the directory...you'll know you're in the correct directory by the prompt, i.e. ..../hplip-1.7.1$

I'm pretty sure it's -p(one).

---

### Post by squig on 2007-02-25
patching file prnt/hpijs/dj3320.cpp

 
is this good? should I proceed with the installation now?

Thanks so much for your help so far. I REALLY appreciate it. When I'm less of an idiot I will definitely put in my time helping other folks out on these forums.

---

### Post by yabbadabbadont on 2007-02-25
> **confused57 said:**
> I think I see your problem you need to be in your actual source directory that was extracted & make sure your patch file is also in the directory...you'll know you're in the correct directory by the prompt, i.e. ..../hplip-1.7.1$

I'm pretty sure it's -p(one).

Oy!  <slaps forehead>  I told you to be in the wrong directory when running the patch.  :oops:  Sorry about that.

---

### Post by squig on 2007-02-25
That is okay. I've learned all about cd and mv. Very exciting.

---

### Post by confused57 on 2007-02-25
> **squig said:**
> patching file prnt/hpijs/dj3320.cpp

 
is this good? should I proceed with the installation now?

Thanks so much for your help so far. I REALLY appreciate it. When I'm less of an idiot I will definitely put in my time helping other folks out on these forums.

I don't see a problem with proceeding...after installing Linux From Scratch, I kind of got the hang of patching & compiling.

---

### Post by squig on 2007-02-25
Wow. The printer is actually working, On the second and third print job!!! Thank you both so much! I have learned about patches, a little bit about what extracting really means, lots of stuff!

---

### Post by confused57 on 2007-02-25
> **squig said:**
> Wow. The printer is actually working, On the second and third print job!!! Thank you both so much! I have learned about patches, a little bit about what extracting really means, lots of stuff!
Glad everything worked for you...there's definitely a learning curve, it does get easier.

Madison, WI is a nice area(in June, Jan was somewhat cold), I traveled to Milwaukee several times due to my job when I "used" to work.

---

### Post by squig on 2007-02-25
I just moved back to WI from Alaska in August, so the winter here is sort of wimpy for me. I'm still like: "So when does it get here....?" Now spring already, almost. 

It's nice country. I missed the farmland a lot when I was "up north."

Thanks again.
~A

---

### Post by Maestro23 on 2007-02-25
> **squig said:**
> I just moved back to WI from Alaska in August, so the winter here is sort of wimpy for me. I'm still like: "So when does it get here....?" Now spring already, almost. 

It's nice country. I missed the farmland a lot when I was "up north."

Thanks again.
~A

I was following this thread.  Glad you got it working.  Learned some stuff didn't you.:)

---

### Post by squig on 2007-02-25
> **Maestro23 said:**
> I was following this thread.  Glad you got it working.  Learned some stuff didn't you.:)

Yes, as you can see; I learned a great deal. I can do it... I just need someone to point me in the right direction once in a while. I'm very happy to be in control of the OS, know what's getting installed, and when. Using XP, I always felt that adding anything--a printer, a camera--there was a piece of software that came with it that was always trying to update, or reminding me to check this, or check that... it was as though the computer wasn't really mine. That is why I changed to Ubuntu. I expected these challenges. But I have been working with an OS LMS for a long time (Moodle) so I understood about the forums and so forth. I understood that people would help out.

I'm very excited to be learning. 
-A

---

### Post by Maestro23 on 2007-02-25
> **squig said:**
> Yes, as you can see; I learned a great deal. I can do it... I just need someone to point me in the right direction once in a while. I'm very happy to be in control of the OS, know what's getting installed, and when. Using XP, I always felt that adding anything--a printer, a camera--there was a piece of software that came with it that was always trying to update, or reminding me to check this, or check that... it was as though the computer wasn't really mine. That is why I changed to Ubuntu. I expected these challenges. But I have been working with an OS LMS for a long time (Moodle) so I understood about the forums and so forth. I understood that people would help out.

I'm very excited to be learning. 
-A

Yeah, it is a good feeling when you get something figured out and working.  You are right, doing stuff this way, you learn your system and if something breaks..how to fix it.

I have been reading all the posts from the guys that used Automatix for setting up just about everything on their systems, and now that their servers are down, they don't know what to do.

Congrats again man and good luck.:guitar:

---

