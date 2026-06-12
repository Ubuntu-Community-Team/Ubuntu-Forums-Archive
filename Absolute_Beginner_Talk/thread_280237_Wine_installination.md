---
title: "Wine installination"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by izacboy_123 on 2006-10-19
Hi!

I followed this guide to install wine:[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

I added the package, then i searched for 'Wine' and i found it! I installed it and nothing went wrong. Is there anything else i need to do before running a windows .exe?

Thanks;)

---

### Post by PriceChild on 2006-10-19
You might want to run ```
winecfg
``` to configure it.
Please be aware that wine is quite a complex program.... don't expect everything to work first time if ever.

You also might want to of installed wine from ubuntu's official repositories instead of any debs from winehq.com

---

### Post by izacboy_123 on 2006-10-19
Thanks for the quick reply!;) 

I ran the code:winecfg

And the settings all look familear. The 'Applications' tab, though i might be wrong. But am i supposed to add the applications i want to be able to run?

E.G:Add("app name","OS to run it as").

Thanks8)

---

### Post by Grey on 2006-10-19
Nope.  Just open the Windows program that you want to use with wine, and it should work.  Wine has actually really improved over the years, and I would have to say that there's a 50/50 chance that the program you want to use will work well enough to do whatever it is that you want to do without a lot of hackery.  (with hackery, odds go up to about 75/25)

---

### Post by izacboy_123 on 2006-10-19
Hi.

I added the .exe i wanted to install to the applications list. Then i double clicked on it. And a message box came up with the following message:
```
Couldn't display "/home/isaac/Desktop/Friendly-Strike2en_Install.exe".
```

I'm guessing i have to configure wine, no?:-k

---

### Post by PriceChild on 2006-10-19
You're not going to like this....

wine is a command line app.
This should work:```
wine /home/isaac/Desktop/"Friendly-Strike2en_Install.exe"
```

---

### Post by izacboy_123 on 2006-10-19
Thankyou pricechild!!!

It worked!:) :-D 

Let's see how i get on;) 

Thanks again!!!!!!8)

---

### Post by izacboy_123 on 2006-10-19
hmm:-k 

The installination worked. But where did the game get installed too? ```
C:\
```

Where's that?

P.S:I'm not really bothered about the terminal. I can simply type:'Wine', then i can drag the filename at the end of the 'wine' code, and put the " on the FileTitle.8)

---

### Post by Grey on 2006-10-19
You can also right click, and open with Wine.  That's how I normally do it, unless I have a problem of some sort.

C:\, according to wine (by default) is in ~/.wine/drive_c/

---

### Post by izacboy_123 on 2006-10-19
:confused: 

Where's '/.wine'?

Sorry if that's a dumb question:(

---

### Post by PriceChild on 2006-10-19
/.wine would be a folder called ".wine" in your root directory.

The actual answer was
~/.wine
~ is a shortcut for your home directory, e.g. for me: /home/pricechild
~/.wine means is a folder called ".wine" inside ~ so /home/pricechild/.wine for example

---

### Post by Grey on 2006-10-19
that's **~**/.wine  ;)

It's a hidden directory, as noted by the . in front of its name.  The tilde (~) represents your home directory.  So to get there from the command line, you might do this:

```

cd ~/.wine/drive_c/Program\ Files/whatever
wine program.exe

```

With Nautilus, you would have to show hidden files and directories to get there.  Or, you could press <ctrl>-L, and type ~/.wine

---

### Post by izacboy_123 on 2006-10-19
Thanks i should be able to get the game working now!;) 

But a HUGE error has happened!!!:o 

when i type :winecfg

The window pops up, but it's super sized!! i have a screen shot for you to look at.

P.S:I blanked out the things i don't want anyone to see8)

---

### Post by Grey on 2006-10-19
System->Preferences->Screen Resolution

:)

---

### Post by izacboy_123 on 2006-10-19
No, it's not screen resolution. It only happens to the winecfg window.

I have another problem come up:( 

I tried running the install program again to get the directory, and it gave me this error:
```
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub

```

...hmm:-k

---

### Post by izacboy_123 on 2006-10-19
Please help. I'm hoping for wine to be up and running by tonight!:o

---

### Post by Grey on 2006-10-19
I've honestly never seen that before, and it seems rather odd.  Try this command.  "wineboot".  It simulates a Windows reboot.  And don't run winecfg anymore.  Once is enough.  :P

---

### Post by izacboy_123 on 2006-10-19
Hi.

I tried "Wineboot". It made a loading sound when i pressed enter. So it must have worked.

I tried running the installer again, but it still gives me that error message:( 
I'll try to cut and paste the installer to another directory, and see what happens.

---

### Post by izacboy_123 on 2006-10-19
Nope:( 

Moving it to another directory doesn't seem to make a difference:(

---

### Post by Grey on 2006-10-19
Okay, enough installing already.  Installing once, and once only should be sufficient.  You just need to go to where it's installed, and run the executable.

---

### Post by Foudre on 2006-10-19
the wine folder is in your home folder, if you mean the one that holds like ther virtual c drive. its a hidden folder, goto  your home folder hit ctrl+H  and it should toggle hidden folders on or off

---

### Post by Foudre on 2006-10-19
i feel dumb, i didn't even notice there was a second page

---

### Post by RedBowers on 2006-10-19
The .wine directory is a hidden directory in your home. If you are viewing it through a terminal code: ls -al and that will list all of the directories including the hidden ones. You can change to that directory just by typing
code: cd ~/.wine

---

