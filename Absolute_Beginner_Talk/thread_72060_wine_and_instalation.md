---
title: "wine and instalation"
date: 2005-10-05
forum: Absolute Beginner Talk
---

### Post by bmarilena on 2005-10-05
Hi everybody,

I just installed ubuntu and succesfully got wine and installed it. I have to install one programme using wine but I don't figure out how.
The progr. is on a cd and has an installer. 
Please, can you help me?

And.... another question.
I have a backup for thunderbird. In windows was easy just copying the folder in the default location.
In linux I have problems locating the directory where to put the folder.... can you sugest me something?

Thanks and sorry for boddering.

Marilena

---

### Post by matthewv on 2005-10-05
Just double-clicking on the setup.exe should start the setup program... if not, right-click and open with "wine"

Your thunderbird profile is most likely in a hidden folder (.mozilla/thunderbird) in your home directory. Just open your home directory and press ctrl+h to view hidden folders

---

### Post by bmarilena on 2005-10-05
Hi again, thanks for the advice.
I have to check the hidden files for thunderbird... but for wine... unfortunately it doesn't work. It starts and after coupe of secconds.... just closes
I don't have enough time to see if has an error code or something....
Pls Help me

Marilena

---

### Post by matthewv on 2005-10-05
[QUOTE=bmarilena]Hi again, thanks for the advice.
I have to check the hidden files for thunderbird... but for wine... unfortunately it doesn't work. It starts and after coupe of secconds.... just closes
I don't have enough time to see if has an error code or something....
Pls Help me
Marilena[/QUOTE]

If you run wine in a terminal
```
wine /media/cdrom/setup.exe
```
then you'll get the error messages. It's most likely just failing, as wine doesn't work with all software and is still alpha software.

---

### Post by bmarilena on 2005-10-05
:) hi againa.... 
For thunderbird it works..... thanks a lot... I'll try again with wine... seems like some packages are not installed, so I'll start again the process...
If any news... Keep contact...
and Thanks again

Marilena

---

### Post by bmarilena on 2005-10-05
again problems with thunderbird...
I got all the contacts and messages, but after I asked get mail... the answer was...
" alert!
Unable to write the email to the mailbox.Make sure the filesystem allows you write privileges and you have enough disk space to copy the mailbox"

I check and there are the privileges for the mozila-thunderbird folder... and 3.4 G looks like nough space for the mailbox.
What else should I do?

Marilena

---

### Post by matthewv on 2005-10-05
[QUOTE=bmarilena]again problems with thunderbird...
I got all the contacts and messages, but after I asked get mail... the answer was...
" alert!
Unable to write the email to the mailbox.Make sure the filesystem allows you write privileges and you have enough disk space to copy the mailbox"
I check and there are the privileges for the mozila-thunderbird folder... and 3.4 G looks like nough space for the mailbox.
What else should I do?
Marilena[/QUOTE]

try running from terminal
```
chmod -R 777 ~/.mozilla/thunderbird
```
that should (hopefully) fix permissions problems

---

### Post by manicka on 2005-10-05
[QUOTE=bmarilena]again problems with thunderbird...
I got all the contacts and messages, but after I asked get mail... the answer was...
" alert!
Unable to write the email to the mailbox.Make sure the filesystem allows you write privileges and you have enough disk space to copy the mailbox"
I check and there are the privileges for the mozila-thunderbird folder... and 3.4 G looks like nough space for the mailbox.
What else should I do?
Marilena[/QUOTE]
If you've copied the folder over from a cd archive then you may have to give read/write premissions to the folder and all it's contents

---

### Post by manicka on 2005-10-05
Also, have you had a look at the wine applications databse at [http://appdb.winehq.org/](http://appdb.winehq.org/) . It may have some pointers for the program you're trying to install.

---

### Post by bmarilena on 2005-10-05
wow..... it works... thanks again....
I'm so happy to use ubuntu...
And appreciate your help
Thanks again
Marilena

---

### Post by manicka on 2005-10-05
enjoy :D

---

### Post by bmarilena on 2005-10-06
Unfortunately the problem with wine still exists...

I had to uninstall and do the steps again....

And I got stuck on installing...

After 

[I]tools/wineinstall
WINE Installer v0.75

~/wine-0.0.20050725-winehq ~/wine-0.0.20050725-winehq/tools
Running configure...

./configure: line 996: config.log: Permission denied

Configure failed, aborting install.[/I]

I was suggested to run the same command as root, but it didn't work either...

What should I do next?

---

### Post by manicka on 2005-10-06
There are debs available for this version of wine. Go the [winehq download]("http://www.winehq.com/site/download") page and follow the instructions for adding the repository and installing wine.

---

### Post by bmarilena on 2005-10-07
I'll try again...
Thanks

Marilena

---

### Post by bmarilena on 2005-10-07
H, I just started over again... but i got this:
[I] # apt-get build-dep wine
Reading package lists... Done
Building dependency tree... Done
E: Build-Depends dependency for wine cannot be satisfied because the package libicu28-dev cannot be found
[/I]
What should I do netx?

Marilena

---

### Post by manicka on 2005-10-07
You don't need to run build-dep

Just

sudo apt-get install wine

---

### Post by bmarilena on 2005-10-08
Is there any problem if after install wine I get the message "11 packages not upgated"?

Anyway I proceded to install.

Marilena

---

### Post by manicka on 2005-10-08
It means you have 11 packages waiting to be upgraded.

Run:-  

sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by bmarilena on 2005-10-08
:) thanks, is updating now, is it ok if the wine is probably installed?

Hope yes...otherwise.... I don't know.

Marilena

---

### Post by bmarilena on 2005-10-09
[QUOTE=matthewv]If you run wine in a terminal
```
wine /media/cdrom/setup.exe
```
then you'll get the error messages. It's most likely just failing, as wine doesn't work with all software and is still alpha software.[/QUOTE]


I tried nad look what happenede:
[I] wine /media/cdrom/setup.exe
Converted windows dir to new entry HKCU\Environment "windir" = L"c:\\windows"
err:thunk:_loadthunk (commctrl.dll, Cctl1632_ThunkData16, comctl32.dll): Unable to load 'commctrl.dll', error 2
err:module:LdrInitializeThunk "comctl32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"D:\\setup.exe" failed, status c0000142
[/I]

What should I do next?

Probably I didn't configure wine correctly, but I can't locate the error.

HELP please

---

### Post by manicka on 2005-10-09
I would suggest going to [http://appdb.winehq.org/](http://appdb.winehq.org/) and seeing if anyone else has attempted to install your program. If so, follow the advice there.

---

### Post by bmarilena on 2005-10-09
Well, I was there and as I supposed nobody installed that application. Is a programme developed for a quite narrow market and everybody's using it under windows...

---

### Post by manicka on 2005-10-09
I guess if no one else has documented how to get it working, then you may be out of luck.

---

### Post by bmarilena on 2005-10-09
Should I go back to windows in this case? Or I can finally manage to make it working with wine?

---

### Post by manicka on 2005-10-09
[QUOTE=bmarilena]Should I go back to windows in this case? Or I can finally manage to make it working with wine?[/QUOTE]
Only you can answer that one

---

### Post by bmarilena on 2005-10-09
Thanks!

I think I'll stay with ubuntu and try to make the programme work. At least for annother while.

---

