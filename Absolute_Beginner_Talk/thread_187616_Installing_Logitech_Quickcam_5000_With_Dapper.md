---
title: "Installing Logitech Quickcam 5000 With Dapper"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by Jah Jah Binks on 2006-06-03
I am fresh off the boat when it comes to Ubuntu and have been unable to follow most of the tutorials around here. I saw a thread that gave a solution to this problem ( [http://ubuntuforums.org/showthread.php?t=118517&highlight=logitech+quickcam+5000](http://ubuntuforums.org/showthread.php?t=118517&highlight=logitech+quickcam+5000) ) but it was as if they were talking about nuclear physics. Can anyone walk me through this process very slowly and patiently?

P.S. While you're at it i wouldn't mind being able to watch a DVD on my system as well.

---

### Post by Jah Jah Binks on 2006-06-03
Alrighty then could someone walk me through this then?

[https://wiki.ubuntu.com/Webcam](https://wiki.ubuntu.com/Webcam)

---

### Post by hanexar on 2006-06-03
Hi, 
 I won't trough the whole processus, but here is some tip for walk through the 
[https://wiki.ubuntu.com/Webcam](https://wiki.ubuntu.com/Webcam)

1- open up a terminal.  You can find it in your application menu.

2- >  Add the following line to your /etc/apt/sources.list

```
deb http://blognux.free.fr/debian unstable main
```

Then you need to update the packages and install easycam 

type in your terminal

```
 sudo gedit /etc/sources.list 
``` and add the line at the end of the document.

3- 
> 
sudo apt-get update
sudo apt-get install easycam2

Type each line followed with an enter in your terminal.

You can do all these steps through the synaptic manager in your admin tool in your system menu.  But it is quicker with the terminal.

I hope it helped

---

### Post by Jah Jah Binks on 2006-06-03
Thanks for the help. Here's what happens when I go to **Applications **----- **Terminal** ---- and type in **/etc/apt/sources.list**:

**bash: /etc/apt/sources.list: Permission denied**

---

### Post by socialSavant on 2006-06-03
I also have a problem with this repository. If I add the line to /etc/apt/sources.list either manually or via Synaptic (same effect I beleive) and then update/reload, I only get this error:
```
Err http://blognux.free.fr unstable/main Packages 404 Not Found
Failed to fetch http://blognux.free.fr/debian/dists/unstable/main/binary-amd64/Packages.gz  404 Not Found
```

I have browsed the site and noticed that its true... this is no binary-amd64/ directory only binary/. Of course, I have the amd-64 kernel so would like a matching package, but wouldnt Easycam work just fine as 32bit app as well? Is there any work-around for this? Do I have to manually install?

Thanks for the help

---

### Post by hanexar on 2006-06-03
[QUOTE=Jah Jah Binks]Thanks for the help. Here's what happens when I go to **Applications **----- **Terminal** ---- and type in **/etc/apt/sources.list**:

**bash: /etc/apt/sources.list: Permission denied**[/QUOTE]

Do

```
sudo gedit /etc/apt/sources.list 
```

Sudo means: Super user do
Gedit is the equivalent of bloc note in windows

You'll get a prompt asking for your password.

SocialSavant: Your package is missing.  Search on the forum or on google if you can find it somewhere else.

---

### Post by Jah Jah Binks on 2006-06-03
Okay this is where I'm at I type **sudo gedit /etc/sources.list** into the terminal and enter my password. It opens a new window **sources.list (/etc) -gedit** that has **deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main** in it. However the initial terminal i typed in now comes up with this:

[B]Audio device open for 44.1Khz, stereo, 16bit failed
Trying 44.1Khz, 8bit stereo.
Audio device open for 44.1Khz, stereo, 8bit failed
Trying 48Khz, 16bit stereo.
Audio device open for 48Khz, stereo,16bit failed
Trying 22.05Khz, 8bit stereo.
Audio device open for 22.05Khz, stereo, 8bit failed
Trying 44.1Khz, 16bit mono.
Audio device open for 44.1Khz, mono, 8bit failed
Trying 22.05Khz, 8bit mono.
Audio device open for 22.05Khz, mono, 8bit failed
Trying 11.025Khz, 8bit stereo.
Audio device open for 11.025Khz, stereo, 8bit failed
Trying 11.025Khz, 8bit mono.
Audio device open for 11.025Khz, mono, 8bit failed
Trying 8.192Khz, 8bit mono.
Audio device open for 8.192Khz, mono, 8bit failed
Trying 8Khz, 8bit mono.
Sound device inadequate for Esound. Fatal.[/B]

---

### Post by MetalMusicAddict on 2006-06-04
Jah, your not doing what hanexar posted.
```
sudo gedit /etc/apt/sources.list
```
Not.
```
sudo gedit /etc/sources.list
```
Read carefully.

---

### Post by socialSavant on 2006-06-06
[QUOTE=hanexar]
SocialSavant: Your package is missing.  Search on the forum or on google if you can find it somewhere else.[/QUOTE]

Thanks, all i needed to know.

---

