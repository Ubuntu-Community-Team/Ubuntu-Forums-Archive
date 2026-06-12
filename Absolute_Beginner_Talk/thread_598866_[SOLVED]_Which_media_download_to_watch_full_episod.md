---
title: "[SOLVED] Which media download to watch full episodes of ABC? 7.10"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by ammmom on 2007-10-31
I want to watch a full episode on ABC in Firefox.  When I try to, I get the following: > Oops
Our new video player is only available for:
Windows 2000/XP/Vista - Internet Explorer, Firefox
Mac - Firefox, Safari
To watch, please download the appropriate browser.Is there  any way to work around that?

Many thanks in advance.

---

### Post by por100pre1 on 2007-10-31
Read [this]("http://ubuntuforums.org/showpost.php?p=3405695&postcount=9").

---

### Post by adamorjames on 2007-10-31
> **ammmom said:**
> I want to watch a full episode on ABC in Firefox.  When I try to, I get the following: Is there  any way to work around that?

Many thanks in advance.

Firefox in Wine?
EDIT: Works for me with Wine. Make sure to install the Flash Player.

---

### Post by ammmom on 2007-10-31
> **por100pre1 said:**
> Read [this]("http://ubuntuforums.org/showpost.php?p=3405695&postcount=9").

Well that stinks! :confused:

---

### Post by por100pre1 on 2007-10-31
> **adamorjames said:**
> Firefox in Wine?

Have you tried that? If so, Does it work? :-k

> **ammmom said:**
> Well that stinks! :confused:

Yes, it stinks!!!

---

### Post by adamorjames on 2007-10-31
It works in Wine.

---

### Post by ammmom on 2007-10-31
> **adamorjames said:**
> It works in Wine.

Can I be really newbie-ish? :confused: How does one work it in Wine? I'll need step-by-step directions. :popcorn:

---

### Post by adamorjames on 2007-10-31
> **ammmom said:**
> Can I be really newbie-ish? :confused: How does one work it in Wine? I'll need step-by-step directions. :popcorn:

ok one sec.

Here is Ubuntu specific instructions, some steps may work in other distros while others won't. Open the terminal by going to the menu at the top left and clicking Applications. In the submenu click Accessories and in that submenu click Terminal.
In the Terminal type this- 
```

sudo apt-get install wine

```
Now, open up the web browser you use and go to this address - 
```

http://www.mozilla.com/en-US/firefox/all.html

```
Select the Windows Firefox download link of your preferred language. Once you are done downloading Firefox for Windows, double click on the file. Wine will open the file and then you just need to install it. Now, at the end of the installation it will ask you if you want to start Firefox and you will click no.
Go to the top left menu and click Applications. In the submenu find Wine and click it, then go to Programs and there you will find Mozilla Firefox.
Now you know how to use Wine. You can now go get the Flash Player exe and install Flash Player. Have fun. After installing Flash Player go to abc.com of course, there will be an install of a plugin or such at abc.com for the video player but it is pretty simple and they give you instructions.

---

### Post by underdog512 on 2007-10-31
before I installed gutsy I had an extension in firefox that an option in tools to "change browser state" in order to emulate other browsers like IE and orpra.  I can't seem to find it now.  does anybody know what I am talking about.  I am pretty sure it resolve this issue without the use of wine.

---

### Post by sstusick on 2007-10-31
IETab extension for Firefox?

---

### Post by adamorjames on 2007-10-31
> **underdog512 said:**
> before I installed gutsy I had an extension in firefox that an option in tools to "change browser state" in order to emulate other browsers like IE and orpra.  I can't seem to find it now.  does anybody know what I am talking about.  I am pretty sure it resolve this issue without the use of wine.

The only thing is that abc.com checks your OS as well.

---

### Post by ammmom on 2007-10-31
> **adamorjames said:**
> 
Here is Ubuntu specific instructions, some steps may work in other distros while others won't. Open the terminal by going to the menu at the top left and clicking Applications. In the submenu click Accessories and in that submenu click Terminal.
In the Terminal type this- 
```

sudo apt-get install wine

```
Now, open up the web browser you use and go to this address - 
```

http://www.mozilla.com/en-US/firefox/all.html

```
Select the Windows Firefox download link of your preferred language. Once you are done downloading Firefox for Windows, did that and it worked great. :)
>  double click on the file. Wine will open the file and then you just need to install it.
Errr, ummm, and, I'm stuck.  :confused: Once I double click on the file I get >  Firefox setup 2.0.0.8.exe cannot be opened.  No application suitable for automatic installation is available for handling this kind of file.  I followed your directions and I downloaded the "windows" firefox download.  Should I have downloaded the "penquin" linux one?

---

### Post by adamorjames on 2007-10-31
> **ammmom said:**
> did that and it worked great. :)

Errr, ummm, and, I'm stuck.  :confused: Once I double click on the file I get  I followed your directions and I downloaded the "windows" firefox download.  Should I have downloaded the "penquin" linux one?

Okay, right click on the Windows Firefox exe file. Click Properties in the right-click menu.  Next, click the Add button. See if you can find Wine in the list of programs, if you cannot then click the arrow to the left of "Use a custom command". In the text box that appears type - 
```

wine

```
Then click Add. Now, try double clicking on the file. If it still doesn't work it most likely means you don't have Wine installed. In which case run the Terminal again, type the line I told you to and see what it says at the end of it trying to install.

---

### Post by ammmom on 2007-10-31
> **adamorjames said:**
> Okay, right click on the Windows Firefox exe file. Click Properties in the right-click menu.  Next, click the Add button (if you don't see Wine Windows Emulator). See if you can find Wine in the list of programs, if you cannot then click the arrow to the left of "Use a custom command". In the text box that appears type - 
```

wine

```
Then click Add. Now, try double clicking on the file. If it still deosn't work it most likely means you don't have Wine installed.
I don't have an "add" button in properties.  I have "basic" 'emblems" "permissions" "open with" and "note"

Thanks in advance for all your help.

---

### Post by adamorjames on 2007-10-31
> **ammmom said:**
> I don't have an "add" button in properties.  I have "basic" 'emblems" "permissions" "open with" and "note"

Thanks in advance for all your help.

Those are the tabs. I must have missed that detail. Go to the "Open With" tab. there you will see Add.  No worries.
EDIT: I'll be waiting for your next post :D

---

### Post by ammmom on 2007-10-31
> **adamorjames said:**
> Those are the tabs. I must have missed that detail. Go to the "Open With" tab. there you will see Add.  No worries.
EDIT: I'll be waiting for your next post :D :lolflag: thank you :lolflag:
I did it!! I figured out the "open with" when I retracked my steps.  Sorry, that I took so long, but thank you again for your patience.

---

### Post by adamorjames on 2007-10-31
> **ammmom said:**
> :lolflag: thank you :lolflag:
I did it!! I figured out the "open with" when I retracked my steps.  Sorry, that I took so long, but thank you again for your patience.

Awesome :) Let me know your progress.

---

### Post by ammmom on 2007-10-31
Maybe I spoke to soon.  The player seems to go, and then stall, and then go, and then stall, etc.  Is that anything that I can correct?? TIA.

---

### Post by adamorjames on 2007-10-31
> **ammmom said:**
> Maybe I spoke to soon.  The player seems to go, and then stall, and then go, and then stall, etc.  Is that anything that I can correct?? TIA.

Ahh, that is what mine was doing. I thought it was just a problem with my internet connection. Not sure :( The only solutions I can see right now would be to either e-mail ABC (like the website maintainer) and tell them that Linux is not included or use VirtualBox. THOUGH you would first want to try the player out on Windows or a Mac to make sure it is or isn't just a Wine problem.

---

### Post by ammmom on 2007-10-31
> **adamorjames said:**
> Ahh, that is what mine was doing. I thought it was just a problem with my internet connection. Not sure :( The only solutions I can see right now would be to either e-mail ABC (like the website maintainer) and tell them that Linux is not included or use VirtualBox. THOUGH you would first want to try the player out on Windows or a Mac to make sure it is or isn't just a Wine problem.

I have a windows xp on my desk as well.  It's doing the same thing, although not nearly as bad.  Annoying, as all.............., But I think that it must be ABC, because their teasers look good.

---

### Post by adamorjames on 2007-10-31
> **ammmom said:**
> I have a windows xp on my desk as well.  It's doing the same thing, although not nearly as bad.  Annoying, as all.............., But I think that it must be ABC, because their teasers look good.

Ahh okay. Well at least you now know how to use WIne. :D Which is used for getting Windows programs to work under Linux. I guess you can mark this thread as "[SOLVED]" in the title.

---

### Post by linuxlizard on 2007-10-31
> before I installed gutsy I had an extension in firefox that an option in tools to "change browser state" in order to emulate other browsers like IE and orpra. I can't seem to find it now. does anybody know what I am talking about. I am pretty sure it resolve this issue without the use of wine.

The extension is called user agent switcher.

Unfortunately it will not work in this case because abc installs a special media player plugin for their site (an exe file) for their tv shows.

---

### Post by adamorjames on 2007-10-31
> **linuxlizard said:**
> The extension is called user agent switcher.

Unfortunately it will not work in this case because abc installs a special media player plugin for their site (an exe file) for their tv shows.

Yes that is the other problem. So... the OS scan and the exe.

---

### Post by VCSkier on 2008-03-10
Is using wine the *only* workaround?  I don't much care for wine.

btw, has everyone who has read this thread submitted feedback?  It's really easy.  If this matters to you at all, please do.  [Here's]("http://dynamic.abc.go.com/streaming/landing?lid=ABCCOMGlobalMenu&lpos=FEP") think link to the list of videos.  Just select one and then click on "Feedback."

---

