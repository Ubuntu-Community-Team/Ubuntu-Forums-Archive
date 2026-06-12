---
title: "A few newb questions/problems from someone new to ubuntu/linux"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by J0E0NE on 2006-06-03
Hello Thankyou for taking the time to read my post;
I have an nvidia geforce 6600gt 128mb and I don't know if the computer is running off that or my chipset, how can i check? I have used synaptic to install nvidia-glx, I believe that is the driver my graphics card needs, if I am wrong or I need some other things too please correct me ;) 

Also My screen resolution is wrong, when i go to system preferances screen resolution the highest option I have to chose from (out of 3 choices) is 1024 * 768 and mine is 1280*1024 so what can I do?

I am a complete newb to linux and ubuntu and am not that good with computers either. Please make your replies newb friendly and explain what to do because I really have no idea how to install things etc... with linux :rolleyes: as I said I'm a complete newb.

Thankyou very much for your time.

---

### Post by nalmeth on 2006-06-03
To add resolution's open a terminal APPLICATIONS --> ACCESSORIES --> TERMINAL
type:
sudo dpkg-reconfigure xserver-xorg

pick the default's for everything unless you know better, and when you get to resolution's, add the extra one's you need.

You may want to do this before enabling glx. You have installed it already, but it's not enabled, so don't be alarmed.. Upon installation, the driver you would be using would be the open-source 'nv' driver. Running the nvidia-glx-enable command will switch it to 'NVIDIA'. 

[Here's]("http://wiki.serios.net/wiki/Ubuntu_NVIDIA_proprietary_display_driver_installation") one of aparently many available howto's for NVIDIA installation. 
Choose the method "through APT", unless you want to go about it the harder way.

---

### Post by edifuzzy on 2006-06-03
"I have an nvidia geforce 6600gt 128mb and I don't know if the computer is running off that or my chipset, how can i check"

Have a look to see where your monitor is connected at the back of the computer, is it connected to your motherboard or a dedicated GFX board?

"Also My screen resolution is wrong, when i go to system preferances screen resolution the highest option I have to chose from (out of 3 choices) is 1024 * 768 and mine is 1280*1024 so what can I do?"

Have a look at this thread...it may help you with your resolution problem.

[http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution]("http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution")

Hope this helps you.

---

### Post by jpkotta on 2006-06-03
[QUOTE=J0E0NE]Hello Thankyou for taking the time to read my post;
I have an nvidia geforce 6600gt 128mb and I don't know if the computer is running off that or my chipset, how can i check? I have used synaptic to install nvidia-glx, I believe that is the driver my graphics card needs, if I am wrong or I need some other things too please correct me ;) 

Also My screen resolution is wrong, when i go to system preferances screen resolution the highest option I have to chose from (out of 3 choices) is 1024 * 768 and mine is 1280*1024 so what can I do?

I am a complete newb to linux and ubuntu and am not that good with computers either. Please make your replies newb friendly and explain what to do because I really have no idea how to install things etc... with linux :rolleyes: as I said I'm a complete newb.

Thankyou very much for your time.[/QUOTE]

You can check with ```
glxinfo
``` and look for NVidia.  If you see Mesa, then you're not running the driver.  Another quick test is ```
glxgears
```  If the gears are slow, you're not running the driver.

---

### Post by J0E0NE on 2006-06-03
[QUOTE=nalmeth]To add resolution's open a terminal APPLICATIONS --> ACCESSORIES --> TERMINAL
type:
sudo dpkg-reconfigure xserver-xorg

pick the default's for everything unless you know better, and when you get to resolution's, add the extra one's you need.[/QUOTE]

I did this and selected the resolution i needed and pressed space and it added a * to it so i guess that meant it was added so i went to the end of the end of the xserver set up and quit the terminal.
I went to the screen resolution selection menu and there was still only three there and not the one i wanted...
didn't it save the changes I made or something?

Thanks for your reply

---

### Post by nalmeth on 2006-06-03
Try restarting the Xserver, or rebooting.

---

### Post by u.b.u.n.t.u on 2006-06-03
Hi J0E0NE,

I had a very similar situation resolved yesterday.

I have a 6600GT too and it is working in 3d now.

Here is my post:

[http://www.ubuntuforums.org/showthread.php?t=187358](http://www.ubuntuforums.org/showthread.php?t=187358)

---

### Post by J0E0NE on 2006-06-04
Ok, Screen resolution is sorted thankyou very much for your help, also I have the nvidia drivers now up and running and that other post about the geforce6600gt really helped:
[QUOTE=jeffc313]if you run
```
glxinfo | grep rendering
```
from terminal and the output is this 
```
direct rendering: Yes
``` then you have 3d acceleration on, if else, it is off[/QUOTE]
i got yes :) everything seems to be working.
Thankyou very much all.

---

### Post by J0E0NE on 2006-06-04
Ill be getting a new ethernet modem from my ISP but in the mean time im stuck with my speedtouch usb 330 modem.
Does any of you know how I could get it working? I checked for drivers in synaptic and found none :( 

Thankyou for all your help and time.

---

### Post by nalmeth on 2006-06-04
Is this a [dial-up modem?]("https://wiki.ubuntu.com/DialupModemHowto")

---

### Post by J0E0NE on 2006-06-04
It is a dial up modem yes, and ill try and get it working with that how-to thankyou very much, Ill keep you up to date.
edit: I can only find scan modem for a previous version of ubuntu, will this work? Also the only driver for it optimized for my processor isn't a .deb file its an rpm so I don't believe It will work.

Can someone help?

Thanks in advance.

---

### Post by 3rdalbum on 2006-06-04
```
sudo apt-get install alien
```

Go into a terminal, navigate to the directory which contains the rpm file, and type:

```
alien name-of-rpm-file.rpm
```

(where name-of-rpm-file.rpm is the actual filename)

```
sudo dpkg -i name-of-new-deb-file.deb
```

I don't know for sure if it will work, but give it a go and make sure you tell us all how it went.

---

### Post by J0E0NE on 2006-06-04
[QUOTE=3rdalbum]Go into a terminal, navigate to the directory which contains the rpm file, [/QUOTE]
I can do the rest but how do I do this?

Thanks

---

### Post by richbarna on 2006-06-04
You can either go to the folder manually and then open a terminal from there.
Or open your terminal and type "cd".(without the comma's)
This means Change Directory.
For example :- cd /home/
You will now be in the home directory.
Any time you are in a directory, you can type "ls", this will then show you what archives, folders, files are there.

---

### Post by J0E0NE on 2006-06-04
Ill try this out and keep you informed, thankyou for your help :D

---

### Post by J0E0NE on 2006-06-04
joe@ubuntu:~$ cd /home/joe/desktop/My Files/
bash: cd: /home/joe/desktop/My: No such file or directory

What could I be doing wrong?

Thanks

---

### Post by J0E0NE on 2006-06-04
Sorry if its a bit off subject but if I installed ubuntu on a sata2 HD would it make much differance from my IDE one it is currently installed on?

Thanks for your time and help.

---

### Post by Solver on 2006-06-04
[QUOTE=J0E0NE]joe@ubuntu:~$ cd /home/joe/desktop/My Files/
bash: cd: /home/joe/desktop/My: No such file or directory

What could I be doing wrong?

Thanks[/QUOTE]

You have a space in your folder name, that's a special character you need to precede with a backslash. So you'd have to do 

```

cd /home/joe/desktop/My\ Files
```

instead. However, you're already in the folder /home/joe, as witnessed by the joe@ubuntu part of the prompt. Hence, you can just do

```

cd desktop/My\ Files

```

Finally, the shell has a very useful autocomplete function. For example, type "cd desktop/M" and hit the Tab key on your keyboard. The shell will automatically complete the folder's name.

---

### Post by J0E0NE on 2006-06-04
joe@ubuntu:~$ cd desktop/My\ Files
bash: cd: desktop/My Files: No such file or directory

also tab just sounded the system alarm with 1 beep edit: and did nothing

Can anyone shed any light on this?

---

### Post by Solver on 2006-06-04
Ah. It has to be Desktop with the capital D, at least that is how it is by default.

Hint: you can also do cd in steps. That is, instead of doing cd Desktop/My\ Files, you can first do cd Desktop, and then cd My\ Files.

---

### Post by J0E0NE on 2006-06-04
I Tried the capital D and also doing it in steps as I was getting frustrated it still comes up with that same no such file or directory :(
edit:
joe@ubuntu:~$ cd /Desktop
bash: cd: /Desktop: No such file or directory

---

### Post by Solver on 2006-06-04
Something else has to be wrong, then. Try the ls command (that's like LS just small letters). It will output the contents of your current directory. Hence you'll see if you have Desktop, desktop, or whatever else the case may be.

---

### Post by aysiu on 2006-06-04
Type ```
cd Desktop
``` and press enter Then type ```
cd M
``` and press tab twice, then Enter. ```
joe@ubuntu:~$ cd Desktop
joe@ubuntu:~/Desktop$ cd My\ Files/
joe@ubuntu:~/Desktop/My Files$
```

---

### Post by J0E0NE on 2006-06-04
ahahahahhahahha YES! 
Finally :D :D :D 
Thankyou aysiu ur a star :KS 
Sorry im a bit excitable but ive  bin tryin to get it to work for a while ;)

Thankyou all

---

### Post by aysiu on 2006-06-04
Those slashes can get confusing. You might also want to (for the future) do ```
cd "Desktop/My Files"
```

---

### Post by J0E0NE on 2006-06-04
Ok wow that surprised me, i converted it to a .deb installed the package and wow no errors all worked :)
So what do I have to do know? edit That is to get the modem recognised or I mean to enable the package? 
What I'm trying to say is now I have the package installed how do I move on?

Thanks in advance.

---

### Post by shamrock_uk on 2006-06-04
Just an FYI so you can understand navigating on the command line, because it's really fast when you get it. 

If you check out the Ubuntu book, which you should find at 

/usr/share/example-content/book-toc.html 

and look in chapter 3, near the bottom there's a nice diagram of the linux filesystem and how it all fits together. Will help you get a feel for navigation. :-)

**cd /**  takes you to the root of the filesystem (where you'll see folders like bin and boot) This is at the top of the pyramid. 

Whenever you do **cd /** it will immediately start looking from the root directory. 

So when you typed **cd /Desktop**, it went right to the top of the filesystem and looked for a desktop folder there, which was why it didn't find it. 

If you're in the same directory as the folder you want to move to then you omit the forward slash. So in your home directory, **cd Desktop** is the correct command as you've discovered to move to your Desktop. 

Similarly, **cd Desktop/"My Files"** or **cd Desktop/My\ Files** would jump you straight to My Files. 

You *can* use the forward slash, as you tried to do, but you then have to specify from the 'top' of the filesystem. So **cd /home/<your username>/Desktop** would have worked.

Don't be put off by the beep on tab completion either (and you can turn it off in the terminal options) - if there are more than one alternative to the filename then it will beep, hit it twice and it'll autocomplete as far as it can. If you type another character in and then tab again, it should pick the correct one.

---

### Post by J0E0NE on 2006-06-04
That is very helpfull thankyou very much :KS 
So now I have managed to convert my package to .deb and i've installed it, do I have to activate it or anything?

---

### Post by shamrock_uk on 2006-06-04
[QUOTE=J0E0NE]That is very helpfull thankyou very much :KS 
So now I have managed to convert my package to .deb and i've installed it, do I have to activate it or anything?[/QUOTE]

You may have to load the driver. Could you post a link to the page you downloaded from please? That will probably help us give you guidance.

---

### Post by J0E0NE on 2006-06-04
Errrm I can't actually remember where I got it from, there are so many sites and I did it like 2 days ago, all I can say is its version:
speedtouch_1.3.1-2_amd64.rpm
that was before converting it to .deb
I hope this helps anyone trying to help me :neutral:

---

### Post by shamrock_uk on 2006-06-04
[QUOTE=J0E0NE]Errrm I can't actually remember where I got it from, there are so many sites and I did it like 2 days ago, all I can say is its version:
speedtouch_1.3.1-2_amd64.rpm
that was before converting it to .deb
I hope this helps anyone trying to help me :neutral:[/QUOTE]

Sorry, you'll have to wait until someone with the modem comes along I'm afraid. 

Although, just checking - that looks like it's for an AMD 64 bit processor - you do have one, right? And that'll probably only work in the 64-bit version of Ubuntu. 

Here's a link to a howto for Ubuntu which will probably be more tailored. 

[http://nyati-buffaloblog.blogspot.com/2006/04/ubuntu-speedtouch-howto.html](http://nyati-buffaloblog.blogspot.com/2006/04/ubuntu-speedtouch-howto.html)

Hope that helps!

I seem to find that the internet is full of Ubuntu howto's as the community is so damn helpful - often a google for **<insert device> ubuntu howto** does wonders. 

Also, purely to make your searching more effective, if you go to [http://www.google.com/linux](http://www.google.com/linux) then you can enjoy a google search stripped of all the non-linux chaff :-)


(Edits)

---

### Post by J0E0NE on 2006-06-04
[QUOTE=shamrock_uk]Sorry, you'll have to wait until someone with the modem comes along I'm afraid. 

Although, just checking - that looks like it's for an AMD 64 bit processor - you do have one, right? And that'll probably only work in the 64-bit version of Ubuntu.[/QUOTE]
Yes I have the linux 64 bit version and yes I have an amd 64bit processor

Thankyou for the howto :) how ever im sorry to say it didn't help me, it was a bit complicated etc I have the package installed I just dont know what to do with it if anything, I guess I'll have to wait for someone with the modem to come along.
Anyones help is apretiated I really need the modem working with ubuntu.

Thankyou very much for everyones help (and thats alot)

edit:
ALCATEL SpeedTouch USB ADSL modem user-space driver
ALCATEL SpeedTouch USB ADSL modem user-space driver. This package contains
all the necessary software to use your SpeedTouch USB modem under Linux. It
currently support only PPPoA encapsulation.

Its version 1.3.1-2

Thats the only information I can give I'm sorry I really dont remember the site I got it from :(

Anyway I hope it helps soemone to help me :)

Thanks in advance.

---

### Post by shamrock_uk on 2006-06-04
[QUOTE=J0E0NE]Yes I have the linux 64 bit version and yes I have an amd 64bit processor[/quote]

Ah good, in that case to save you waiting, I'll try and cherry-pick a little from that howto and make it easier to understand.

It looks like (by installing the rpm) you've basically reached stage 2. 

So on to stage 3:

> Step 3: configure the software
You are now going to load the pppoatm module, and set up your machine so the pppoatm module is loaded at every boot

The "pppoatm module" is basically a driver for your modem. A module is a cunning way to easily add and remove drivers from your kernel on the fly without having to restart the computer (whereas in Windows for comparison, a new device = restart). Think of the kernel as being the 'core' that runs everything else (and windows has a kernel too, by the way, you just only see it when there's a problem ;)) The funny name isn't so strange - ppp stands for point-to-point protocol and is basically what your modem uses. 

Now, you want to load the module - this is done with the 'modprobe' command. **modprobe xxxxx** loads a driver and **modprobe -r ** removes it. 

So would you please open up a terminal and try the following:

```
sudo modprobe pppoatm
```

And let us know what happens. :-) 

Edit: If nothing happens, that's good - in Linux, no message is always good news.

---

### Post by J0E0NE on 2006-06-05
Im pleased to say nothing happened
Can anyone please tell me what to do next :) I must be so close :D

Thanks in advance.

---

### Post by J0E0NE on 2006-06-05
Actually never mind, I've just doubled my speed with my ISP and they're sending me an ethernet modem which should solve all these USB problems.
Id just like to say thanks to everyone who has helped me with these problems =D> 

Thanks all

---

### Post by shamrock_uk on 2006-06-05
Hokay, but you're very close - you just have to copy and paste some text into a few config files as per the walkthrough. If the ethernet modem takes a while to show up, it'll be easy to finish up.

---

### Post by J0E0NE on 2006-06-09
Yup all solved Ive now got the modem and it worked imediatly

---

