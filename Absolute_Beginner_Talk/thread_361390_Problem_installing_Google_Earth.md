---
title: "Problem installing Google Earth"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-02-14
I've tried installing Google Earth for Linux. The file "GoogleEarthLinux.bin download to my desktop. I dbl-clicked it and it appears to install. I have installed libglade2-ruby as instructed on another thread. I've tried running Synaptic with the command: chmod +x GoogleEarth.bin.  I copy and pasted the Synaptic line from the thread mentioned above. I checked Synaptic and I find nothing under Google. All I find is the word Google.

I get this response back from Synaptic:
[I]kittyhawk63@kittyhawk63:~$ chmod +x GoogleEarth.bin
chmod: cannot access `GoogleEarth.bin': No such file or directory
kittyhawk63@kittyhawk63:~$
[/I]

I would appreciate any suggestions to get this resolved. Thanks in advance.

---

### Post by charles.g.moore on 2007-02-14
If you have automatix installed I would just use that, I installed it that way and it fired right up.

---

### Post by kittyhawk63 on 2007-02-14
How do I make a "Home Directory?
Here is what Terminal gives me.

chown: cannot access `/home/kittyhawk63/.local/share/applications/googleearth.de sktop': No such file or directory
kittyhawk63@kittyhawk63:~$

---

### Post by Rhubarb on 2007-02-14
You're very close, but you've made a few errors in installing it there.

Your GoogleEarth.bin is actually residing in ~/Desktop, so to get it all running nicely, this is what you need to do in the Terminal:
```
mv Desktop/GoogleEarth.bin ~
```

Then follow everything from (and including) "sudo sh GoogleEarthLinux.bin"
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Google_Earth](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Google_Earth)

Another thing to note, is that your reference to "Synaptic" is actually the Terminal (Applications --> Accessories --> Terminal)

You'll need some recent video card drivers to run google earth - which no doubt you may discover after you've installed it.

Edit: You've all ready got a home directory, it's /home/kittyhawk63/
a tilda (~) can also represent your home directory.  So when you see "kittyhawk63@kittyhawk63:~$" It means that you're in the home directory.

---

### Post by kittyhawk63 on 2007-02-14
Got back this error:

kittyhawk63@kittyhawk63:~$ mv Desktop/GoogleEarth.bin ~
mv: cannot stat `Desktop/GoogleEarth.bin': No such file or directory
kittyhawk63@kittyhawk63:~$

---

### Post by kittyhawk63 on 2007-02-14
Trouble installing Automax

---

### Post by Rhubarb on 2007-02-14
ok, in that case your downloaded google earth installer is floating around somewhere else in your system.
Nevermind, it's probably best to start from scratch again.

Your best bit is to follow all the instructions from
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Google_Earth](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Google_Earth)

The first command you type in the terminal (from the ubuntuguide howto),
wget -c [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
will download google earth to your home directory.

Edit: I have never tried Automatix, so unfortunantly I can't help you there.

---

### Post by kittyhawk63 on 2007-02-14
Edit: You've all ready got a home directory, it's /home/kittyhawk63/
a tilda (~) can also represent your home directory. So when you see "kittyhawk63@kittyhawk63:~$" It means that you're in the home directory.

The problem is that I am continually being told that I have no home directory even when I see "kittyhawk63@kittyhawk63:~$". :confused: Thanks for making this clear. I am so new to Ubuntu that I have to relearn a lot of commonly known stuff in Windows after working with it for the last two decades. I hope that you will stay with me until this is resolved. I am learning a lot in a short space of time. I am keeping notes and bookmarking all referenced web pages.

---

### Post by kittyhawk63 on 2007-02-14
Thanks for this. I will do it.

---

### Post by Rhubarb on 2007-02-14
> **kittyhawk63 said:**
> How do I make a "Home Directory?
Here is what Terminal gives me.

chown: cannot access `/home/kittyhawk63/.local/share/applications/googleearth.de sktop': No such file or directory
kittyhawk63@kittyhawk63:~$

The error here just states that the file googleearth.desktop does not exist, and / or the path /home/kittyhawk63/.local/share/applications/ does not exist.

Hmmm, I think you've made a bit of a mistake with doing your chown command back there.
This directory and file name is located here:
/usr/local/share/applications/googleearth.desktop

When you put a "/" in the front, it means you're referring to the full path of the file / directory.
If you omit the "/" at the front, it means you are referring to that directory / file relative to where you currently are (which is typically in your home directory, ~ , which is located in /home/kittyhawk63/

---

### Post by kittyhawk63 on 2007-02-14
Rhubarb,
Thanks for clearing this up. I feel like I've landed on a new planet. I've been on planet Gates far too long and had been experiencing oxygen deprivation. All this fresh air is making me light headed. :) 
kittyhawk63

---

### Post by Maestro23 on 2007-02-14
> **kittyhawk63 said:**
> Rhubarb,
Thanks for clearing this up. I feel like I've landed on a new planet. I've been on planet Gates far too long and had been experiencing oxygen deprivation. All this fresh air is making me light headed. :) 
kittyhawk63

Glad you got straighten out.  I was reading back thru your posts.  Don't get installing from Synaptic(GUI) confused with installing from source(like your .bin file).  Synaptic is used for installing stuff from the Ubuntu Repositories, not for installing .tar or .bin files(source).

Just some more FYI.

---

### Post by kittyhawk63 on 2007-02-14
Maestro23,
Thanks for this bit of information. Wish I had learned this the first day last week. Everything all in good time. Right? :) 
Thanks again,
kittyhawk63

---

### Post by Rhubarb on 2007-02-15
> **Maestro23 said:**
> Glad you got straighten out.  I was reading back thru your posts.  Don't get installing from Synaptic(GUI) confused with installing from source(like your .bin file).  Synaptic is used for installing stuff from the Ubuntu Repositories, not for installing .tar or .bin files(source).

Just some more FYI.
I know .tar files are usually source code files, but I didn't think .bin ones are (google earth isn't open source).
I'm taking an educated guess that .bin files are binary files (precompiled program).

Hmmm, anyway, it's not a big issue (probably a misunderstanding).

@kittyhawk63: There's quite a few different ways to install stuff in Linux.
No doubt as you go along you'll bump into all sorts of cool things Linux can do (I'm learning the Python programming language at the moment - simply beautiful!)

---

### Post by kittyhawk63 on 2007-02-15
Thanks Rhubarb.

---

### Post by RichPicker on 2007-03-01
Confused.

I downloaded and uncompressed GoogleEarth, and used it for a few minutes. Then quit.

But it is NOT under Applications > Internet.

If I open the folder /usr/local/googleearth, and double-click the application icon, it launches and works. But what did I do wrong that it is not included under Applications > Internet?

---

### Post by Maestro23 on 2007-03-01
> **Rhubarb said:**
> I know .tar files are usually source code files, but I didn't think .bin ones are (google earth isn't open source).
I'm taking an educated guess that .bin files are binary files (precompiled program).

Hmmm, anyway, it's not a big issue (probably a misunderstanding).

@kittyhawk63: There's quite a few different ways to install stuff in Linux.
No doubt as you go along you'll bump into all sorts of cool things Linux can do (I'm learning the Python programming language at the moment - simply beautiful!)

Yeah, you are right Rhu, I was thinking about his compiling from source and typing something else.  Need to lay of the Killian's Irish Red when I come to the fourms.:) 

Thanks for the correction man.

---

