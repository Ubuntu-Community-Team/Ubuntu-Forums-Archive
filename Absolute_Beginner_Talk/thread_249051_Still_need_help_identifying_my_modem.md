---
title: "Still need help identifying my modem"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2006-09-02
scanModem either isn't working properly on my comp, or i don't understand how it works. It's supposed to produce a text file called modemData.txt, which it doesn't. I suspect that I simply haven't gotten it to work properly, and partly that may have something to do with it not being called scanModem, but rather scanMomdemSept1. Do I have a zip utility with the package install of Ubuntu 6.06? If not with an app, what line command do i need to open scanmodem file? Thank you very much in advance.
 Ricardo

---

### Post by Metacarpal on 2006-09-02
Hi.  If you post a request for assistance and it isn't answered within 15 minutes, just wait a little while.  Don't post a new thread.  It actually lowers the likelihood that someone will help you.

Just hang out and wait for someone with modem experience to come along.  I'd help you but I don't know modem setup.  While you're waiting, use the search feature - there are plenty of helpful threads out there already.

It can occasionally take as long as a day to get a knowledgeable answer.  If you don't get a response within several hours to a day, you should post a reply to your own, existing thread updating it with what you've tried.

---

### Post by ricardisimo on 2006-09-02
> **Metacarpal said:**
> Hi.  If you post a request for assistance and it isn't answered within 15 minutes, just wait a little while.  Don't post a new thread.  It actually lowers the likelihood that someone will help you.

Just hang out and wait for someone with modem experience to come along.  I'd help you but I don't know modem setup.  While you're waiting, use the search feature - there are plenty of helpful threads out there already.

It can occasionally take as long as a day to get a knowledgeable answer.  If you don't get a response within several hours to a day, you should post a reply to your own, existing thread updating it with what you've tried.

Gotcha. Sorry about that. Specialization makes sense, and I should have guessed that would play a big part. So, different question: to enter command lines, do I go to applications > Terminal? Just want to make sure I'm experimenting in the right places. Thanks.

---

### Post by lemmy999 on 2006-09-02
Yes, to open a terminal go to Applications/Terminal. Type scanmodem and it should open the app. I can't help too much as i don't use a modem

Have you tried searching on this forum using "scanmodem" as your search term? There are a number of hits for it. Just read thru some of the hits and see what you can learn. In the meantime you may get someone knowledgeable who can help.

---

### Post by ricardisimo on 2006-09-02
> **lemmy999 said:**
> Yes, to open a terminal go to Applications/Terminal. Type scanmodem and it should open the app. I can't help too much as i don't use a modem

Have you tried searching on this forum using "scanmodem" as your search term? There are a number of hits for it. Just read thru some of the hits and see what you can learn. In the meantime you may get someone knowledgeable who can help.

Thanks for replying. Yeah, there's a lot for "scanmodem", but nothing for "scanMomdemSept1", which is the app everyone earlier today was pointing me towards. Something's up, don't know what. I'll just keep plugging away. Tell me something: why doesn't Ubuntu know exactly what's connected to it, even if it doesn't know how to communicate with it? When I go to "Computer" only the drives are listed. Why is that? Why not empty ports, or the USBs or the graphics card, or the modem with which it can't communicate? How do i "look" at these in Ubuntu?

---

### Post by ricardisimo on 2006-09-02
So this program I got from Linmodems, the scanMomdemSept1, is an x-shellscript application which opens with text editor. That can't be right, or can it? This would explain why what I see looks like C++ or some other program language, rather than the output from any actual analysis it's done of my modem's chipset. What SHOULD it open with, and any guesses as to why it's set to open in gedit?

---

### Post by annda on 2006-09-02
if it's a script, you need to tell your system that it should be executed, rather than read (after all, scripts are just text files). in terminal, go to where the script is and type:

```
chmod +x scanMomdemSept1
```

then you shoud be able to run the script.

---

### Post by ieee488 on 2006-09-02
I just went through the process this morning.

If you go to [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
and scroll down, it explains exactly what commands you need to do.

If you don't follow the commands, and double-click on the scanModem.gz file as we like to do in Windows, you will get the scanMomdemSept1 file instead of just a file named scanModem.

Anyway, good luck with that.

---

### Post by ricardisimo on 2006-09-02
> **ieee488 said:**
> I just went through the process this morning.

If you go to [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
and scroll down, it explains exactly what commands you need to do.

If you don't follow the commands, and double-click on the scanModem.gz file as we like to do in Windows, you will get the scanMomdemSept1 file instead of just a file named scanModem.

Anyway, good luck with that.

It says something about downloading onto other OSs, and sure enough I'm doing it on my friend's Mac. Is that the issue? What am I missing, though?

---

### Post by ieee488 on 2006-09-02
You just need to scroll down to the part that talks about how to install and run scanModem.

But since you write that you have given up on this...
It may be just as well since most modems are not going to work with Linux. I lucked out, and my modem does.

---

### Post by ricardisimo on 2006-09-05
> **ieee488 said:**
> You just need to scroll down to the part that talks about how to install and run scanModem.

But since you write that you have given up on this...
It may be just as well since most modems are not going to work with Linux. I lucked out, and my modem does.

Well, since wireless is going at least as badly as my other options, here I am right back at modems...
I guess I'm missing something really obvious, because I've scrolled down both the Linmodems page and the modemHowto page, and I still can't even get ANYWHERE near a file named scanModem. It simply won't download onto my friend's Mac as "scanModem.gz", so unless I'm simply supposed to rename it, which I doubt...
Here's my new question: since this tool is clearly meant to be some sort of shortcut to get the required information from my comp and OS, and since there's nothing short about this shortcut, can someone give me whatever would be the long way to get my chipset info off of my modem. I thank you all in advance.

---

### Post by ieee488 on 2006-09-05
You don't have another computer to use that has Windows? One at work?

When I downloaded scanModem.gz into Windows 2000, I didn't have any problems. Then I copied it onto a floppy and copied the file to my /home directory in Ubuntu.

I'm still on dial-up so getting my modem to work in Ubuntu was top priority for me. I also bought an used external modem on eBay for $10; new ones cost $30-40. If you don't want to hassle with scanModem etc, this may be the thing to do. You'll want to make sure you buy one that has a serial connection.

---

### Post by ricardisimo on 2006-09-20
OK. I partitioned my comp at home to give this a try there as well. "gunzip" doesn't work on either machine in the terminal window. I just get the same message: "No such file or directory", and the other commands from the Linmodems instructions don't work at all either. However, on the home machine I could either just launch the archive through GUI or drag and drop the file (scanModem.gz) into the terminal window and extract it to the Desktop. I double-clicked the resulting file on the desktop and got the needed results: a folder called "Modem" full of very useful text files. On this, my work computer: _nothing._ I can GUI a file called "scanModemSept20", or whatever the latest version is, but this file opens in Gedit. The other listed option is to open with an HTML editor, which I doubt will be of any use. What ***should*** be opening this file? TIA.

---

### Post by ricardisimo on 2006-09-22
> **ricardisimo said:**
> OK. I partitioned my comp at home to give this a try there as well. "gunzip" doesn't work on either machine in the terminal window. I just get the same message: "No such file or directory", and the other commands from the Linmodems instructions don't work at all either. However, on the home machine I could either just launch the archive through GUI or drag and drop the file (scanModem.gz) into the terminal window and extract it to the Desktop. I double-clicked the resulting file on the desktop and got the needed results: a folder called "Modem" full of very useful text files. On this, my work computer: _nothing._ I can GUI a file called "scanModemSept20", or whatever the latest version is, but this file opens in Gedit. The other listed option is to open with an HTML editor, which I doubt will be of any use. What ***should*** be opening this file? TIA.

In the meantime, I've done the obvious and gone home to check out the properties on the scanModem tool on that comp, and it says it's a script that opens with a text editor, so I'm at a loss. Any suggestions are appreciated. Thanks.

---

### Post by ieee488 on 2006-09-22
scanModem.gz is Linux version of a zip file

When you unzip it, you get a file named [COLOR="Magenta"]scanModem[/COLOR]
then when you execute the *chmod +x scanModem* command, scanModem becomes executable; it is similar to a batch file from the DOS days in that you can see the commands it runs

maybe that's what causing all the confusion

I've run the commands from the DialupModemHowTo on installations of Ubuntu on two different PCs and both times it has worked flawlessly

You're probably getting the file not found error because you are not in the same directory as the scanModem.gz file.

---

### Post by ricardisimo on 2006-09-22
> **ieee488 said:**
> scanModem.gz is Linux version of a zip file

When you unzip it, you get a file named [COLOR="Magenta"]scanModem[/COLOR]
then when you execute the *chmod +x scanModem* command, scanModem becomes executable; it is similar to a batch file from the DOS days in that you can see the commands it runs

maybe that's what causing all the confusion

I've run the commands from the DialupModemHowTo on installations of Ubuntu on two different PCs and both times it has worked flawlessly

You're probably getting the file not found error because you are not in the same directory as the scanModem.gz file.

The file's on the desktop, and the terminal claims to be at my desktop. Is there a search function within terminal to make sure?

---

### Post by someonedumb on 2006-09-23
Use the "ls" command to view the contents of the current directory.

---

### Post by ricardisimo on 2006-09-23
> **someonedumb said:**
> Use the "ls" command to view the contents of the current directory.

Thanks! That did the trick. I'm still not quite sure how it can say it's in "Desktop" when in fact it's in the "Home" folder. Now we'll see if the kindly folks at Linmodems can help me out.

By the way, how does one navigate within the terminal to this or that folder? I didn't bother doing that; I simply copied the archive to it's current location.

---

