---
title: "My first experiences"
date: 2005-05-29
forum: Absolute Beginner Talk
---

### Post by Yoeri on 2005-05-29
I am a web-developer for five years, working in a complete Microsoft environment. I also use the same environment at home, because there was too many software that kept me using Windows, I never thought of switching to Linux. Recently, I stopped using Outlook and replaced it with Thunderbird, also stopped using IE and started using Firefox ... also Visual Sourcesafe was replaced by Subversion. The only thing remaining was .NET. I read an article over on OSNews about a MonoLive cd, which I tried, and it convinced me to make a complete switch to Linux on my home laptop.

So far the brief history on how I started using Ubuntu ...

My experiences as a Windows-user and a complete Linux noob:

**Installation:**
The setup went very well, all hardware detected without any problem. I just missed an option to select the packages I want to install. Don't need to install AGP and additional IDE drivers which are required by Windows. 
The first boot went alright, no annoying startup movies like in Window XP Professional. A clean desktop, just the way I like it.

**Usage**
- I have several problems using Linux. One big problem is the way to install software. I downloaded Java JRE 1.5 from the Sun website, and double clicked the .bin file. It was a no go ... a big red stop icon with a long text saying that I cannot execute the file ... off to google and search how to get JRE installed  :-? several searches and command-line statements further, I managed to get it installed, without knowing what I did ...
- I also wanted to get rid of the software I don't want, so I went to Add/Remove programs and deselected the software ... It uninstalled everything, but did not remove the Icons from the programs menu, and I cannot find a way to delete them manually (I am really a noob  :roll: ).
- After some searches on the internet, I managed to install Thunderbird 1.0.2 (via command-line as root). I wanted to copy my windows-profile to the Linux machine (file-sharing with a Windows network works great  :grin: ), but I got the message I could not copy the files because I did not have the right permlissions  :-| 

After the TBird story, I decided to put back my Windows hard-drive, and post my experiences. I think I'll read some Linux guides before giving it another try ...


Firefox, Thunderbird and Mono made it possible for me to make the swith, but I find myself lacking some knowledge to do basic Linux stuff  :-| ...

---

### Post by UbuWu on 2005-05-29
Take a look at ubuntuguide.org for most of your problems.

---

### Post by mohaham on 2005-05-29
For help on installing Mono you might want to look here..
[http://www.ubuntuforums.org/showthread.php?t=31518&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=31518&page=1&pp=10)

For help on other stuff the best place is..
[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by Yoeri on 2005-05-29
Trying to get mono installed right now ...  :) 

I just configured a VMWare machine with Ubuntu to try everything out before installing everything on my portable again ...

---

### Post by Error_Msg on 2005-05-29
Ubuntu How Come is a good tutorial to get your feet wet too!

E_M

---

### Post by Jenda on 2005-05-29
> - I have several problems using Linux. One big problem is the way to install software. I downloaded Java JRE 1.5 from the Sun website, and double clicked the .bin file. It was a no go ... a big red stop icon with a long text saying that I cannot execute the file ... off to google and search how to get JRE installed  several searches and command-line statements further, I managed to get it installed, without knowing what I did ...
For this you use synaptic or apt-get. The Starter guide is the perfect resource.
> - I also wanted to get rid of the software I don't want, so I went to Add/Remove programs and deselected the software ... It uninstalled everything, but did not remove the Icons from the programs menu, and I cannot find a way to delete them manually (I am really a noob ).
Sorry, also a n00b, but I'm sure I saw a glimpse of this on the forums...
[http://ubuntuforums.org/showthread.php?t=36479](http://ubuntuforums.org/showthread.php?t=36479)
[http://ubuntuforums.org/showthread.php?t=35331](http://ubuntuforums.org/showthread.php?t=35331)
[http://ubuntuforums.org/showthread.php?t=34139](http://ubuntuforums.org/showthread.php?t=34139)
[http://ubuntuforums.org/showthread.php?t=33041](http://ubuntuforums.org/showthread.php?t=33041)
might be of some help...
> - After some searches on the internet, I managed to install Thunderbird 1.0.2 (via command-line as root). I wanted to copy my windows-profile to the Linux machine (file-sharing with a Windows network works great ), but I got the message I could not copy the files because I did not have the right permlissions
Are you sure you weren't attempting to write on the win partition? They usually don't like that  (Linux cannot write NTFS).

---

