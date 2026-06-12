---
title: "Linux Real Player 10 Error Please Help"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by AnnaMary on 2007-07-30
I have been trying off and on for 8 hours now to get RealPlayer for Linux to work.  I have read many posts and tried various sets of instructions.  I have only had Ubuntu for a few days, so I realize that I am worse than a newbie, but here goes:

I managed to download RealPlayer10GOLD.bin to my desktop.  The Properties tell me that it is indeed executable.  When I click on the icon, I get this error message:  Cannot open /home/anna/Desktop/RealPlayer10GOLD.bin: No application suitable for automatic installation is available for handling this kind of file.

Undaunted, I looked around for some more directions and found some for the command line/terminal (same thing?)  There I typed --->sudo ./realplayer10GOLD.bin, entered my password, and was told --->   sudo: ./realplayer10GOLD.bin:  command not found

Obviously not understanding the cues, I then typed --->sudo chmod realplayer10GOLD.bin, and was told --->chmod:  missing operand after 'realplayer10GOLD.bin' Try 'chmod --help' for more information.

Trying to follow more directions on yet another post, I typed --->chmod a+x realplayer10GOLD.bin, and was told --->chmod:  cannot access 'realplayer10GOLD.bin': No such file or directory

Okay, earlier in the day I tried to install something along the lines of good/bad/restriced w32 codecs???  didn't help

I hope I have given enough information so that someone can recognize what I should do next.  Many, many thanks for your time reading and/or responding to my post.

Other than this, I have managed to get Ubuntu to do all of what I am looking for.  (Funny how checking a bunch of boxes and clicking install works wonders!)  I could never manage to do it again,  because I don't know what I checked off and applied!

RealPlayer for Linux......here I come......eventually........

---

### Post by oldos2er on 2007-07-30
[QUOTE=AnnaMary;3102887]to follow more directions on yet another post, I typed --->chmod a+x realplayer10GOLD.bin, and was told --->chmod:  cannot access 'realplayer10GOLD.bin': No such file or directory

 You were so close! Linux (including Ubuntu) is case-sensitive, so change to the directory where you have RealPlayer10GOLD.bin and try that again:

 chmod a+x RealPlayer10GOLD.bin 

 Once you do that, try running

 sh RealPlayer10GOLD.bin 

and see what happens. you may need to put "sudo" in front of that last command--I don't recall.

 Hope this helps a little.

---

### Post by tomcheng76 on 2007-07-30
also
please
run this
```

cd /home/anna/Desktop
chmod a+x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin

```

the " . " mean current directory ,  while " .. " means the parent directory
when you run
```

pwd

```

you will know where is your current directory
so, ensure you located at /home/anna/Desktop before running sudo ./RealPlayer10GOLD.bin
thats why you need cd /home/anna/Desktop (enter this directory)

---

### Post by tomcheng76 on 2007-07-30
also , i want to point out this thing too
why sudo ./RealPlayer10GOLD.bin  need to add "./" but chmod a+x RealPlayer10GOLD.bin doesnt ?!!!!!

it is because terminal run executable by finding the executable name in environment variable PATH
type this
```

echo $PATH

```

you will know what is your PATH variable storing
as /home/anna/Desktop is always not inside PATH
therefore, you need the full path of the executable in order to operate
that is /home/anna/Desktop/RealPlayer10GOLD.bin 
or a relative path
that is if you are located in /home/anna/Desktop/
./RealPlayer10GOLD.bin  is the same as /home/anna/Desktop/RealPlayer10GOLD.bin

---

### Post by AnnaMary on 2007-07-30
Everyone,

Thank you for your help and patience.  I can now just about do everything I need to in Ubuntu.  Real Player is working, though I can't play stations from Radio Pass.  I found that another application in Ubuntu that I must have gotten by accident works better.  Yet, I can use Real Player to listen to some of the daily radio programs I really like, but couldn't get any other way.  Again, thank you, thank you!

---

