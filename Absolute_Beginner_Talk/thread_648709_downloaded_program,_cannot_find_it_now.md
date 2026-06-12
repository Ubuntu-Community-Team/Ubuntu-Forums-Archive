---
title: "downloaded program, cannot find it now"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by geezer_wheelz on 2007-12-23
Good day everyone

I have spent the last few hours reading posts and been unable to find the answers I need. Before i get frustrated and stick my Windows hotswap drive in I thought I would ask for some help.
I am running Kubuntu 6.06 LTS
I downloaded firefox, thought I saved it to the desktop, but was unable to find it on the desktop.
Went to find files, found a firefox file, two of them actually, one was on the install CD but it was a Windows install package.
The other one was 4096 in size, (the file I downloaded was 14mb) double clicked on it and found a file that said it was an installer, tried to open it with Add remove programs, got nowhere, open it and it is a bunch of text, or something.
Read a bunch more stuff on this forum, went to terminal and typed &#8220;&#8221;which firefox&#8221;&#8221;, then I posted this!!

I need to know how to find  files I  have downloaded, and I need to know how to run the install process

I found lots of ideas on this forum but they were all for different versions of Linux and did not seem to work for Kubuntu.

I really want to make this work. but I hate being stupid!! :confused:

Any help will be greatly appreciated!
Chad

** Edit **
I got the find files function to work for me, it is not like windows and you cannot type in part of the name, I was typing in just firefox, it was finding nothing for me.
When I typed in the full name of the file it found it for me, firefox-2.0.0.11.tar.gz
Still cannot figure out how to install it though :(

---

### Post by Steve Zenone on 2007-12-23
What application, or webbrowser, are you using to download Firefox with (e.g., Konqueror which is default in Kubuntu)? Konqueror will give you the option to "Save As". You get to tell it where to save the download. However, since you're just looking at moving away from your current browser to Firefox, look at [http://ubuntuforums.org/showthread.php?t=330386]("http://ubuntuforums.org/showthread.php?t=330386").

---

### Post by PinkFloyd102489 on 2007-12-23
Checked your home folder?

---

### Post by meindian523 on 2007-12-23
Number 1:You don't need to download software off the net to install on Linux....specially those like Firefox,you just go to Applications>>Add/Remove

Search for Firefox and check the box and click apply.That's all...


Try looking for it in your home folder ("/home/username") or Downloads folder(if Kubuntu creates one,Mandriva does)

---

### Post by Ertai87 on 2007-12-23
I'm not sure if I can help with your downloading issue, but at least on Gutsy (I don't know how it works on Kubuntu but I presume it's the same if it derives from Ubuntu), you can install most applications by using apt-get.  If you want to install a program, type:

sudo apt-get install [program-name]

So, for example, Firefox would be "sudo apt-get install firefox".  You can install almost anything this way without having to go through the hassle of downloading from mozilla.com or whatever.  Also, .exe files generally don't run properly in Linux, as they were built to run on Windows (mostly).  If you want to install something in Linux, you'd generally look for the tar version (.tar.gz extension), which you then unzip and execute one of the files in the unzip by chmodding it and then ./-ing it.

---

### Post by califman831 on 2007-12-23
Firefox can be installed using the regular package manager (add/software) or the full blown version of adept found under system in the task manager.  Firefox itself downloads to the desktop by default unless you change it uner edit/preferences.

---

### Post by meindian523 on 2007-12-23
@Ertai

Usually,mozilla.com detects your localization and OS,so it's unlikely that the OP would have downloaded the .exe

---

### Post by Ertai87 on 2007-12-23
Ah, after reading your edit, this should be the solution, try it out and let me know how it goes (note these instructions will work for Ubuntu Gutsy, so the syntax might be different in Kubuntu, but the general idea is the same):

1) Unzip the tar.gz to somewhere (desktop is fine).

2) In terminal, surf to desktop (or wherever you unzipped to) and run "chmod +x [installer name]".  You may have to sudo the chmod but probably not.

3) Run "./[installer name]".

By default, runnable files are not recognized as runnable when you unzip them from tars, so you have to make it executable by using chmod +x, and then run it using ./.  For more information on chmod, check the man pages.  The basic idea is that it adds (+) or removes (-) read (r), write (w), and execute (x) permissions to various files.

@meindian: Ah.  I kinda assumed when he said "it opens as a bunch of text" that he downloaded the wrong installer.  Upon rereading the post, I was mistaken, sorry! XD

---

### Post by geezer_wheelz on 2007-12-23
Thank you everyone for your help!!

I will use add remove programs from now on.

Does it also work for drivers as well?
I found the dual core driver on the AMD site, but I really need some video drivers. I have 2 7600GT cards in SLI mode, and I cannot seem to get any more resolution than 1024x768.
Using Konquerer with this silly side panel I have to move the window from side to side to read the whole page!!

Thanks much all!

**Edit**
Thanks Ertai87 I will do the suggested reading

Learning like crazy here!!!
I have firefox installed and working, and using it right now, Thank you for the tip!!
Downloaded the AMD driver and made a folder and unzipped it into that folder.
Thats all folks! Now I have to do some reading to figure out Ertai87's advice. 
Was going so good there for a minute!
:)

---

### Post by geezer_wheelz on 2007-12-24
This is too much for my drug addled mind!
I am on some serious pain killers (oxy-contin 320mb twice a day) from a surgery I just had and not much of this is making sense to me right now.
I think I will have to live with my 1024x768 until I get off these pills

But thank you all for the help, I did make some progress, At least until I tried to figure out how to install drivers!!

Wishing you all a merry Christmas and a safe New Year!!

I'll be back  :)

---

### Post by hyper_ch on 2007-12-24
Btw, don't you want to install gutsy instead of dapper? Dapper is getting old and there's been a huge improvement meanwhile.

---

### Post by euthyfro on 2007-12-24
well, i'm running gutsy & anything i download in firefox just doesn't show up where i save it or anywhere else for that matter.  the "downloads" window doesn't even open.  when i go to re-download it because i don't have what i thought i downloaded it lists the file in the "save to..." window but it isn't there when i browse to that location, also, the "downloads" window under tools is completely empty.  i know my connection is fine because i can get stuff from torrents & browse internet well enough.

---

### Post by sailor2001 on 2007-12-24
most of your programs you could find in /usr/bin   Some apps do not have an installer in them..also you could do it in terminal 'sudo apt-get install [program]' or clicking alt-f2 and inserting the program.. and of course as suggested look in your places/homefolder ctrl/h

---

