---
title: "[SOLVED] Problem installing a program in Wine"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-08-22
I have a dual boot (XP/Feisty) and am trying to install a program in Wine. It's a search program called Electronic Edition 7.0 that comes with a database of text files which it searches at your request.

I do have the program on CD, but had already installed it on XP. So I thought I would just install it by using that. I am getting in error in my terminal command. Perhaps someone can tell me why-- here below is the code (The first effort below has spaces between words. Terminal did not seem to like that, so I tried underscores but it is still not finding the .exe file I want it to point to):
```


krpa@Baba-desktop:~$ wine /media/disk/Program Files/Electronic Edition 7/Windows/Search/EE7Search.exe
wine: cannot find '/media/disk/Program'
krpa@Baba-desktop:~$ wine /media/disk/Program_Files/Electronic_Edition_7/Windows/Search/EE7Search.exe
wine: cannot find '/media/disk/Program_Files/Electronic_Edition_7/Windows/Search/EE7Search.exe'
```

Related question: In general, if one has a CD of a program is it better to install into wine from that? Or is it the same thing whether one installs from the CD or from an already installed version in Windows?

---

### Post by toidi on 2007-08-22
Have you tried putting quotations around the target ie ```
wine "/media/disk/Program Files/Electronic Edition 7/Windows/Search/EE7Search.exe"
```

Also make sure that you have full control over your windows partition and not just read permissions.

Easiest way I found to use wine with any program is run the installer from the cd or download by doing a "wine (path to target file)setup.exe.
When I am prompted for an install directory I always change it to install to /home/dan/wineap/ (dan being my user dir).
That way when I want to run something just fire up the terminal and.

```
cd wineap/program dir
wine programname.exe
```

Worked every time for me.

---

### Post by Vadi on 2007-08-22
I don't think the fact that you have the program installed on XP makes much of a difference, since it's a different patrition... albeit Ubuntu can still see it.

I would personally in your case use the Wine File (located in applications -> accessories), find the .exe on the CD and install it from the CD.

But I'm no expert yet :/

---

### Post by Majorix on 2007-08-22
> **Vadi said:**
> I don't think the fact that you have the program installed on XP makes much of a difference, since it's a different patrition... albeit Ubuntu can still see it.

I would personally in your case use the Wine File (located in applications -> accessories), find the .exe on the CD and install it from the CD.

But I'm no expert yet :/

You are right. By directly running the program in a Windows partition, you are disregarding registry entries. And without the registry entries, you can't have full control over your software (like configurations likely getting lost and being unable to patch the program).

I would install the program with Wine on Ubuntu again.

---

### Post by swarup on 2007-08-22
Following is in reply to Toidi's post above.

I put quotes around the windows pathway as you suggested, and it worked perfectly. The only thing is, to my surprise instead of actually installing the program into Feisty, it ran the program and the program opened perfectly, ready to go. 

But can't I INSTALL the program into Feisty using this process? I thought that's what I saw on the website, that one can take an already installed program from windows and use it to install the same program into Feisty. 

I already did this once before on another computer. So one doesn't actually need the installer CD to get it loaded onto Feisty, does one?

---

### Post by Majorix on 2007-08-22
You can't install a program that way. Where did you read about it?

Well you could copy the installation directory under the virtual drive of wine, and find the registration entries from somewhere, thats how you can install it.

---

### Post by swarup on 2007-08-22
> **Majorix said:**
> You are right. By directly running the program in a Windows partition, you are disregarding registry entries. And without the registry entries, you can't have full control over your software (like configurations likely getting lost and being unable to patch the program).

I would install the program with Wine on Ubuntu again.

Yes, yes. That is just what I want to do. But I was thinking that it can be done through the already installed program in the Windows partition. Am I wrong about this?

I want to install the program on Ubuntu.

Do I have two options?
1. Install from previously existing (ie previously installed) Windows program
2. Install from Installer CD

Is this correct?

---

### Post by toidi on 2007-08-22
If the program works perfectly in your windows partition then it appears there is no worries with the registry, as lots of programs in windows don't use the registry except to put up shortcuts on the desktop etc.

You wouldn't be able to install the program to feisty as such, mainly due to the program is already installed and the installer is more than likely left on the CD, thus a reinstall from the CD would be needed.  

You can however just copy the directory over to your feisty install ie to home/dan/wineap/
or to '.wine/drive_c/Program files/" (to see the .wine dir in an explorer window you need to have enabled 'show hidden files' in the view option at the top).

That way you can do it the 'lazy way' as I suggested above.

---

### Post by swarup on 2007-08-22
> **Majorix said:**
> You can't install a program that way. Where did you read about it?

Well you could copy the installation directory under the virtual drive of wine, and find the registration entries from somewhere, thats how you can install it.

I've read so many web pages about this, I've forgotten now where I saw it. But I do have on my laptop, one program which is installed on Feisty (at least it seems like its installed on Feisty--it has a startup icon on the desktop, and runs fine) in this way. That is on a Win98/Feisty dual boot machine.

Anyhow, I'll take your recommendation and try it from the Installer CD and see how that goes instead. I would do it using "Wine File" in Applications -> Accessories?

---

### Post by Majorix on 2007-08-22
There are many ways to run a .exe file, and one of them is the one you said, yes.

---

### Post by toidi on 2007-08-22
Also you can do a quick
```
cd /media/cdrom
```

Then

```
wine setup.exe
```

From the terminal.

---

### Post by swarup on 2007-08-22
> **toidi said:**
> Also you can do a quick
```
cd /media/cdrom
```

Then

```
wine setup.exe
```

From the terminal.

I see. But I assume the "setup.exe" would have to be whatever that file were called in that program ie if that program's executable file were called "install.exe", then one would type that, right? 

Wherever the .exe file is located on the CD, it will find it. One does not need to specify the path to the .exe file?

---

### Post by Vadi on 2007-08-22
Yes to the question about the name of the .exe file, you need to change it accordingly.

As for the second question - that's what the first command, "cd /media/cdrom" does. The **cd** command opens whatever directory is provided, so in this case it'll go into media, and then cdrom. So if the path to the .exe is different, you'd need to change it accordingly after the cd command.

Also, a few tips - doing "cd /" will take you to the "begining" of your ubuntu. To go into a directory, you can just type "cd <directory name>". To view all stuff in a directory, you can do "ls".

---

### Post by toidi on 2007-08-22
You assume correctly in the first instance, sometimes it may be called install.exe.

This is true for most cases but you may have to hunt the subdirs if the main installer is not in the root of the cd. A simple 'dir' in the terminal will pull up all the files and folders in the cd root.

You could try:

```
wine autorun.inf
```

When you are in the root, I have never tried this though, so I cannot say for certain it will work.

---

### Post by Majorix on 2007-08-22
A few points:
*Don't cd to the directory where the exe is located. Its best to run it from your home directory, like this for example:
```
wine /media/cdrom/setup.exe
```
*"wine autorun.inf" will NOT work as that file is just a text file and wine can only run windows executables.
*wine will only look where you point it to. So it will not search the cd for the setup file.

---

### Post by TeaSwigger on 2007-08-22
> Related question: In general, if one has a CD of a program is it better to install into wine from that? Or is it the same thing whether one installs from the CD or from an already installed version in Windows?

In general yes, for one reason because of possible registry entries, which may contain data relevant to the Windows environment and not Linux, even via WINE. Better yet in some cases, if installing from the CD proves to have issues, one might copy the CD as an image file to the hard drive and mount the image, and install from there. :)

You might be interested in looking at this guide, which describes a possible method of moving a windows program to linux as is and running it in WINE:
[http://luiscosio.com/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper](http://luiscosio.com/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper)

Note the different components to copy; not merely the program files but also other directories in other areas and registry keys that are needed for the program to be "fooled" into running in the WINE environment. There are many details which could cause this to fail, and make you install it fresh anyway. So it's a choice of methods but in general just try a fresh install :)

About the syntax in your code:

```
wine /media/disk/Program Files/Electronic Edition 7/Windows/Search/EE7Search.exe
```

You'd need to use "escapes" from blank spaces like so:

```
wine /media/disk/Program\ Files/Electronic\ Edition\ 7/Windows/Search/EE7Search.exe
```

because Linux doesn't like blank spaces in command paths like that. The path doesn't look right; sure it's not

```
wine /dev/scd0/EE7Search.exe
```

or something like that? If that's the Program Files directory copied from a Windows install, it probably won't work without the rest of the installed structure like config files from Documents and Settings, registry entries and so on. 

Post back with any questions and good luck :)

---

### Post by swarup on 2007-08-24
Thanks to the help I've received from you all, I understood the basics of wine function and was able to successfully install my first wine program. It works perfectly.

Now, I do have two follow-up questions:

1. There is another program I want to install: an HTMLeditor called Evrsoft Firstpage 2006. I have the installer on a CD. I also downloaded the same installer off the web, and have it on my desktop (Feisty Gnome). 

The problem is, that the installer is a zip file. The setup-exe is there right inside the zip file, but WINE FILE cannot see inside the zip file, and it cannot open the zipfile. I know the setup.exe file is the first thing you get inside the zip file because I tried right-clicking on it on the desktop, and the Ubuntu Unpackager (or whatever it is called) opens the zip file and shows the setup.exe file right there. I just can't get WINE FILE to point to that setup.exe.

So my question is, how does WINE FILE work with installers which are in a zip format?

2. I have Ubuntu Feisty installed on two computers. A desktop, and a laptop. When I installed Wine on the desktop computer, in Applications -> Accessories there is the application called WINE FILE. However, on my laptop I installed Wine, but there is no such application there. I know Wine is installed because (1) it is listed as such in Add-Remove programs, and (2) I was able to install one program which is on the Windows side of the dual boot. I right-clicked on it, and it offered to install using wine. So I did and it worked. But the Wine File application is not listed in the Accessories. How can I get it there?

---

### Post by Vadi on 2007-08-24
1) Unzip that zip file! Yes, wine can't see it. There's probably a command to have it unzip, but the easiest way is to right click on the file, and select "Exctract Here". Voila, now point wine to that.

2) Right click on Applications top-left, select "Edit Menu's". Poke about there (just click on Applications on your left side really), you should be able to find the Wine File entry - just check it off and it'll appear on applications now.

---

### Post by swarup on 2007-08-24
> **Vadi said:**
> 1) Unzip that zip file! Yes, wine can't see it. There's probably a command to have it unzip, but the easiest way is to right click on the file, and select "Exctract Here". Voila, now point wine to that.

2) Right click on Applications top-left, select "Edit Menu's". Poke about there (just click on Applications on your left side really), you should be able to find the Wine File entry - just check it off and it'll appear on applications now.

1. Yes, it worked. I don't know how I overlooked it. 

The program installed, and placed a start-up icon on the desktop. When I double-click on the icon, it begins the loading process and a "loading" insignia shows up on the desktop, but it doesn't seem to be able to fully load. Can you suggest anything to try? It's a pretty light weight program and should open easily and quickly.

2. I tried looking in Edit Menus and opened all the various options I could find, but did not see the option for the Wine File utility. There was a "File Browser" available for use in the Accessories, butI tried that and it is just the Ubuntu file browser. Any other suggestions?

---

### Post by Vadi on 2007-08-24
1) Give me a moment - I'll try installing it myself.

2) What I did was just associate all .exe files with Wine, so I don'y need to use the Wine File anymore. Here's how you do it:

Right click on the file, select Properties, then select the Open With tab on top. Click the **+Add** button, another menu will pop up. In that menu, at the bottom it'll say "Use a custom command" - click on the little triangle to show a line where you can type. In there, simply type **wine**, then click add, and you're done! Now double-clicking any .exe file should automatically use wine to open it.

---

### Post by Vadi on 2007-08-24
Oh, heh, this is a weird issue.

Actually, what happens is that Wine says that it needs Gecko to install - but that little window is -behind- the loading splashscreen, so you don't see it. I was only able to see it because of a plugin I have in Compiz tha allows me to see all windows on screen.

Here's what you do: after you open the program again, alt+tab to the Wine Gecko installer. The splash screen will still be covering it, but that's not a worry. All you need to do now is press the Tab key to select install (it's on cancel by default), and press enter. Wait some, wine will install gecko, and the program will fully load.

Tell me how it goes.

---

### Post by swarup on 2007-08-24
> **Vadi said:**
> Oh, heh, this is a weird issue.

Actually, what happens is that Wine says that it needs Gecko to install - but that little window is -behind- the loading splashscreen, so you don't see it. I was only able to see it because of a plugin I have in Compiz tha allows me to see all windows on screen.

Here's what you do: after you open the program again, alt+tab to the Wine Gecko installer. The splash screen will still be covering it, but that's not a worry. All you need to do now is press the Tab key to select install (it's on cancel by default), and press enter. Wait some, wine will install gecko, and the program will fully load.

Tell me how it goes.

That is very kind of you to have checked this for me.

I followed the directions you have given above, and this is what happened:

I first double-clicked on the start-up icon. Then the splash screen saying "loading" comes up. Then I  pressed alt+tab. Upon doing that, a small window would appear over the splash screen which says "Gecko Install". But I soon as I let go of alt+tab, that screen disappears. Despite the fact that the Gecko screen had disappeared, I tried pressing tab followed by enter, but nothing seemed to happen. The splash screen just stayed there. So I ended up trying alt+tab, and then various combinations of alt, tab, enter. But nothing happened. I'll try reboot the computer and doing it again (the splash screen is still stuck on the desktop), but it didn't seem to work.


==> I take it back. I just tried it again and it worked. The application has opened, and seems to be working fine. The only odd thing is that when I click on the upper-right "x" to close the application, it doesn't seem to close. It just sits there on the desktop. Did it close for you?

---

### Post by Vadi on 2007-08-24
Aah wait! I told you, the splash screen over-rides the gecko install window. You did right by pressing tab and enter, but you were supposed to wait while gecko installed. Eventually it will and the splash will go away, and the program waits.

By the way: a quick way to reset your ubuntu that I found out was to press ctrl+alt+backspase. Or just alt+backspace, I forget which. I takes you back to the login screen, you can just login, and your previous programs that were working okay will load up.

---

### Post by swarup on 2007-08-24
You are just full of good ideas and suggestions. 

You have helped me solve three different matters--

1. I did try loading the program again, the way you said, and now it is working just wonderfully. The splash screen does go away. And it also closes down just fine. Everything is working.

2. Your suggestion about dealing with Wine on my other computer which doesn't have the wine file in the applications menu, is perfect. Actually, I did what you said and opened clicked on properites and then "open with", and to my surprise the Wine Windows Emulator was already listed there. 

As you described, there was also the option to type something in a window below by the triangle under "custom", but I'm not sure it is needed right? It seems wine has already set itself as the default "open with" for .exe files. I guess that should be all I need?

3. Your suggestion about how to reset the desktop is very helpful. I shall try it. If it saves time in not having to reboot, then that is great. Thanks so much!

---

### Post by Vadi on 2007-08-24
Ahh perfect. Click on 'Thread Tools' near the top and select 'Mark Thread as Solved'.

As for the custom command I was talking about, that is fine, but for the future I've provided screenshots:

[http://vperetokin.googlepages.com/Screenshot-AddApplication.png](http://vperetokin.googlepages.com/Screenshot-AddApplication.png)

[http://vperetokin.googlepages.com/Screenshot-AddApplication-1.png](http://vperetokin.googlepages.com/Screenshot-AddApplication-1.png)

---

### Post by swarup on 2007-08-24
Thank you very much.

I did understand correctly, that so long as under "open with" the default is listed there as Wine Windows Emulator, then I don't need to do anything extra, right? It'll just open and install using wine when I double click on it? And if it says it under this application, then it should do the same for all others it sees of type ".exe", right?

---

### Post by Vadi on 2007-08-24
I think so. PM me if it doesn't work.

---

