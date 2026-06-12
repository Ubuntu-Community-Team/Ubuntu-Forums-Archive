---
title: "Finding my admin account??? HELP!"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by Orillian on 2005-12-05
Ok, here is the deal. I did my install today, everything went great. started playing around and was having fun...alll good sofar.

I then decided to try installing some of my hardware drivers that had not already been installed....my ATI drivers for example. :)

I downloaded the driver off the ATI website. went into the terminal accessed the file and do : su <filename> and it unpacked the file...so far so good. Once unpacked the file tried to install...it hung and then about 15-20 seconds later it pops up a dialog that tells me I need to install from my super user account......WTH?

I thought the account I had set up was the Admin account. Now I go to the user groups section etc.. and the only user I can find in my current user.

I've tried everything I can think of and I've searched high and low, and I'm thinking it's something simple that I've missed but the final word is...I'm stuck! can't find my way into my own darn admin account! :P oops! 

HELP! Anyone! 

This is my first Linux install, I've used UNix systems at school and at work, but I've never had or needed admin access in any of them, and I have no clue how to find it. :P

Note: I tried creating another user and I tried to add him to admin group and root group and a few others and I tried giving him access to admin abilities in the options...or what I thought might work and nothing. Every user I create or use keeps popping up this happy little dialog that tells me I'm not the Super User. :)

O.

---

### Post by IdolizingStewie on 2005-12-05
Ubuntu is set up such that it doesn't have an actual admin account, or root, as it is called in Linux. Instead you usually perform actions that require a superuser by typing sudo before the command. It will ask you for a password. Type in your own password. It will not appear in the terminal, not even as asterisks. This is normal - it's a security measure. Trust that it is being entered. Note that this is also the password you would enter if you needed superuser privileges in a GUI application such as Synaptic.

---

### Post by Orillian on 2005-12-05
ok, I'm a bit lost with the sudo command. I was trying to use it and well long story short I think I fargged something up! :P

> richard@Orillian:~$ sudo su ati-driver-installer-8.19.10-i386.run
Unknown id: ati-driver-installer-8.19.10-i386.run
richard@Orillian:~$

ok I tried the above and it gave me the Unknown id: <filename> error


> richard@Orillian:~$ sudo ati-driver-installer-8.19.10-i386.run
Password:
sudo: ati-driver-installer-8.19.10-i386.run: command not found


this actually asked me for a password but told me the command was not found! 

I know I'm missing something important, but I'm drawing a blank! been reading so much stuff the last two nites my eyes are starting to bug out of my head. :P

Any more help would be most apreciated.

O.

---

### Post by Orillian on 2005-12-05
Just a side note. EVERY time I try just the su <filename> on the ATI driver package, I get the Unknown id: error.

I can't even get back to the point were the su <filename> unpacked the file then told me I needed super user status. ARGGG.. :P ok! so I think I'm an idiot. 

[SIZE="1"]help![/SIZE]:confused: :confused: :confused: 

O.

---

### Post by spin1078 on 2005-12-05
ok, you can type sudo ati-driverblahblah.run isnt a command line because its not an exectuable I believe.  Im new to this too.  another thing you can use is 

sudo -s

this allows you to become the root user.

exit

will bring you back to oyur own account.  the .run Im not sure about.  shot in the dark but you might be able to make it an executable with chmod +x *filename*

now Im new to Linux as well so I might be wrong on that.

then once it is an executable 
./*filename*
should run the executable.

---

### Post by spin1078 on 2005-12-05
say the file was imafile.bin

it would be 
sudo chmod +x imafile.bin (to make it an executable)
sudo ./imafile.bin

---

### Post by spin1078 on 2005-12-05
someone will be able to tell you what a .run files is, I cant cause Im just a beginner too. 

 the sudo -s command is helpful in Ubuntu though.

---

### Post by spin1078 on 2005-12-05
i am all that is post whore. :D

---

### Post by cilynx on 2005-12-05
*.run is a B.S. extension that commercial vendors like to use.  Basically, it means you can run it assuming the permissions are set to executable.  *.bin is the same idea, except "bin" stands for "binary".  Most *.run files that I've seen contain both script (bash, perl, awk, whatever) as well as binary (compiled program code) information.  It seems to be the format of choice for commercial drivers and the like.

---

### Post by Nequeo on 2005-12-05
Hi Orillian,

Two things! Firstly, why are you trying to install the ATI driver off the website? Please forgive me if you have a specific reason for downloading the web version, but if you haven't already tried it, please click on System--->Administration--->Synaptic Package Manager

When it asks for a password, enter your regular password. Then click on 'search' and search for 'xorg-driver-fglrx'. Right click on it, select 'mark for installation' then hit 'apply'. 

And it will download and install the drivers for you! When you're using Ubuntu, try to get out of the habit of googling for software and downloading files. Search synaptic first. It takes care of the downloading and installing and dependencies for you, and will make sure you don't break anything by accident. 

Just bear in mind that after installing fglrx driver, you'll still need to modify your xorg.conf file... but I'm sure the docs you got off their website explain how to do that. If not, just ask here and we'll tell you :)

Okay. Now here is the reason why the command you were typing wasn't working. When you try to run a program... But you don't tell Linux where that program is, Linux will search your 'path' to see if it can find it. Type "echo $PATH" at the command-line to see what your path is.

So, if you're trying to run a file that's not in your path... you need to tell Linux where it is. Even if you're in the same directory as the file! So you could try typing 'sudo ./ati-driver-installer-8.19.10-i386.run' 

The './' just means look in your current directory for the file to run. But as I said above, don't run that installer unless you absolutely need to! Otherwise, just use Synaptic to install the driver.

Cheers,

---

### Post by Pwn* on 2005-12-05
help i just got linux ubuntu to and have the same problem trying to install a demo version of cedga i get to .... > max@diane:~$ sudo su .home/max/desktop/cedgatimedemo/cedega_timedemo_installer.sh
Password:
Unknown id: .home/max/desktop/cedgatimedemo/cedega_timedemo_installer.sh
 i keep getting unknown id o.O i an a complete noob and i would love to learn

*note* my file is a *.sh  file 

its funny i was just about to post a thread and i saw this one :D

---

### Post by Orillian on 2005-12-05
Ah, thanks all for the tips! :) 

Nequeo: Regarding the "xorg-driver-fglrx", I'd hate to say it..but I'd never have know in a million years this was the ATI drivers! :P I'll give that a go ASAP! I really do like all the auto install options that ubuntu has, this has been my only serious sticky point sofar. :)

I got what your saying regarding the file location as well. Tks! 

cilynx: thanks for the heads up.

spin1078: hey I don't mind all your posts...kept my issue at the top of the list on the forum! woot! :) thanks for the help btw.

O.

PS: I'll let you guys know how it goes! :P

---

### Post by Pwn* on 2005-12-05
> Nequeo: Regarding the "xorg-driver-fglrx", I'd hate to say it..but I'd never have know in a million years this was the ATI drivers! lmao neither would i accept for my freind told me that was it not to long ago because he was haveing a similar problem with getting drivers 

anyway why do i kep getting the invalid id thingy is there  a fix im sure it will help both me and Orillian in the near future when we cannot find what we are looking for in the package manager

---

### Post by Nequeo on 2005-12-05
Heh... No worries. 

I'm lucky, I have an Nvidia card, and the driver package is called 'nvidia-glx'. Simple, hey? And you don't need to edit xorg by hand, either. You just run 'nvidia-glx-config enable' after you've installed them. 

I only knew what the ATI drivers were called because I've read so many posts about people complaining about ATI issues. 

You raise a good point, though. There are still many wonderful features in Ubuntu that a casual user won't spot, because they aren't 'advertised' in any way. Sure, there's a complete desktop guide under 'Help' - but how many people read that? :)

Good luck, and keep us posted.

Pwn*: Try "sudo ~/Desktop/cedgatimedemo/cedega_timedemo_installer.sh"

We just want 'sudo', not 'sudo su' (which won't work, and is redundant besides!). Also, 'Desktop' has to have a capital 'D', as Linux is case sensitive. '~' is a shortcut for your home directory. So you can replace /home/max/ with ~. 

Cheers,

---

### Post by Orillian on 2005-12-05
ok got the drivers re-installed! They are showing properly...BUT! the re-install does not fix my actual problem! hanging and crashing of one particular screensaver with ants walking inside balls. :( dang thing hangs my system every time, and it hangs up my screensaver menu since it's selected and it previews.

I was hoping the re-install of the ATI drivers would fix this! kinda wierd that it hangs though, I've got a 9200SE in that machine! Sigh.

[thread here! ]("http://ubuntuforums.org/showthread.php?t=99201")

Thanks for your help though fellas! 

O.

---

### Post by Nequeo on 2005-12-05
Ahh...

Read the thread. It very likely is a video card problem causing the screen-saver to hang. ATI and Linux don't really mix well at the moment, so I wouldn't be surprised. 

Luckily, Linux wouldn't be Linux unless you could disable your screensaver from the command-line!

Open up a terminal, and type in 'gedit .xscreensaver'. (And if you don't already know, don't forget you can hit 'tab' at any time and it will attempt to fill out the rest of the file name, or show you the remaining options. Try it and see.)

Note: You could also use 'vi' or 'nano' instead of 'gedit', if you want that authentic console flavour!

Now... scroll down about a page and look for the lines

```

mode:       <something>
selected:   <some number>

```

And change it so it reads

```

mode:      blank
selected:  <don't need to change this bit>

```

Then save and quit. And that's it. Now your screen will blank instead of showing a 3D screen-saver and hanging.

You could always just uninstall the xscreensaver program, too, but I don't reccomend that, as it is part of the core Ubuntu desktop, and you'll need to remember to reinstall it in the future if you ever want to automatically upgrade to the next version of Ubuntu. 

Cheers,

---

### Post by Orillian on 2005-12-06
See now that's the way to go for now! Thank you! 

I'm not actually using the ubuntu installed machine as anything more then a BOINC server ATM. so simply editing the screensaver config will work fine for now! If I ever decide to do 3d stuff....I'll look into the why of the graphics hang! Tks! 

O.

---

### Post by chilebeans on 2005-12-06
Orillian

There is a post I believe that's in the 2nd or 3rd page (if not near) that explains all the linux commands. I think these commands would help you out.

---

### Post by jwd45244 on 2005-12-06
A couple of people have said that they tried the sudo commands thusly:

sudo su <some command>

The correct way would be:

sudo <some command>

The system will prompt for a password, use your standard user password

---

### Post by Pwn* on 2005-12-06
i tried > ~/Desktop/cedgatimedemo/cedega_timedemo_installer.sh

now i get another error > command not found
look > max@diane:~$ sudo ~/Desktop/cedgatimedemo/cedega_timedemo_installer.sh
Password:
sudo: /home/max/Desktop/cedgatimedemo/cedega_timedemo_installer.sh: command not found


bah what the heck do i do i am reay confuzeded

---

### Post by jwd45244 on 2005-12-06
sudo chmod +x ~/Desktop/cedgatimedemo/cedega_timedemo_installer.sh

sudo ~/Desktop/cedgatimedemo/cedega_timedemo_installer.sh

---

### Post by Pwn* on 2005-12-06
ok got it working and the little installer ran but came to an error !!!

> max@diane:~/Desktop/cedegatimedemo$ ./cedega_timedemo_installer.sh
Verifying archive integrity... All good.
Uncompressing Cedega Time Demo.......................................................................................................................................................................................................
/home/max/.setup8496: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory


it seems as if i dont have libgtk-1.2.so.0 and i searched package manager it found nothing it found alot of other libgtk's though

---

### Post by jwd45244 on 2005-12-06
The libgtk the program expects is not installed.  Go into Synaptic and seach on libgtk to see what version is installed and if ther is an update availble (you may have to reload you repositories lists ( icon on tool bar )

---

### Post by Pwn* on 2005-12-06
uhh it looks like i have the newest one but the installer is asking for an older one herees a screeen [[IMG]http://img425.imageshack.us/img425/9466/screenshot2rv.th.png[/IMG]](http://img425.imageshack.us/my.php?image=screenshot2rv.png)

---

