---
title: "Streamtuner"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2006-04-29
Hi!

Anyone here familiar with Streamtuner?

I been using it to listen to live365. 

My question is really about its recording function. When i click on record a terminal opens and starts recording to or with nanocaster? i've done sudo apt-cache search nanocaster which tells me i haven't got it on my computer.

So, then where if at all is the music being 'ripped' to?
or how might i do so?

any help with this much appreciated as usual,

--
sophtpaw

---

### Post by ali_bongos_dad on 2006-04-29
I've just tried live365 myself and although I'm not a subscriber I did find one or two channels which permitted listenening and recording. The music was ripped to a file in my Home Folder.  
Nanocaster is the live365 server.

---

### Post by Rinzwind on 2006-04-29
Your home directory.

An example:

/home/rinzwind
rinzwind@discworld:~$ ls
**-977 The 80s Channel (80s Grooves)**  downloads  muziek
Desktop                             films      wallpapers
rinzwind@discworld:~$

Stupid thing is Terminal doesn't let me inside the directory :D
edit: nautilus let me in and delete it tho :)

---

### Post by Rinzwind on 2006-04-29
Not to highjack your topic but I used shoutcast and not live365.
The last one shows html at the radiostations. Weird. Anyone know why?

---

### Post by sophtpaw on 2006-04-29
[QUOTE=ali_bongos_dad]I've just tried live365 myself and although I'm not a subscriber I did find one or two channels which permitted listenening and recording. The music was ripped to a file in my Home Folder.  
Nanocaster is the live365 server.[/QUOTE]


Thx, but what file was it saved to? I have looked before and again in my Home folder and it is not visibible to me. Aguess, i don't know what i am looking for

-
sophtpaw

---

### Post by Rinzwind on 2006-04-29
It did when I used live365.

Look:

rinzwind@discworld:~$ ls
Desktop  downloads  films  **Live365 Operator 14914**  muziek  wallpapers
rinzwind@discworld:~$


/home/rinzwind/Live365 Operator 14914/incomplete
rinzwind@discworld:~/Live365 Operator 14914/incomplete$ ls -l
total 96
-rw-r--r-- 1 rinzwind rinzwind 91136 2006-04-29 13:39  - .mp3
rinzwind@discworld:~/Live365 Operator 14914/incomplete$

---

### Post by sophtpaw on 2006-04-29
[QUOTE=Rinzwind]It did when I used live365.

Look:

rinzwind@discworld:~$ ls
Desktop  downloads  films  **Live365 Operator 14914**  muziek  wallpapers
rinzwind@discworld:~$


/home/rinzwind/Live365 Operator 14914/incomplete
rinzwind@discworld:~/Live365 Operator 14914/incomplete$ ls -l
total 96
-rw-r--r-- 1 rinzwind rinzwind 91136 2006-04-29 13:39  - .mp3
rinzwind@discworld:~/Live365 Operator 14914/incomplete$[/QUOTE]

Hi,

Not sure what youre telling me. Have you found where the ripped music is saved to? 
Yes, i do see Live365 Operator 14914 in my home/conrad directories but there is no music saved there,

any help anyone?

--
sophtpaw

---

### Post by Rinzwind on 2006-04-29
Aha.

Well I took the 1st station I saw and recorded and posted the location I found the .MP3 file it was making.

When did you hit the escape inside the terminal popup? If it was when it was still buffering you will not have a music file.

Cuz the file -should- be inside your directory. It should be :P

---

### Post by sophtpaw on 2006-04-29
[QUOTE=Rinzwind]Aha.

Well I took the 1st station I saw and recorded and posted the location I found the .MP3 file it was making.

When did you hit the escape inside the terminal popup? If it was when it was still buffering you will not have a music file.

Cuz the file -should- be inside your directory. It should be :P[/QUOTE]

how do i exit properly?

yes, the way i stop recording is to simply click X for exit. Are you saying that that means i will not save a music file?

--
sophtpaw

---

