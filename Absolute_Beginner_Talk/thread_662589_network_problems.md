---
title: "network problems"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by arvindenrique on 2008-01-09
i have configured network in ubuntu and it worked for me for a few days. but now it doesnt work. the settings are same. the network is working fine in windows XP? whats the problem?

---

### Post by rkd on 2008-01-09
It could be lots of things.

When you say Windows works okay, do you mean that the computer is shared between Windows and Ubuntu? Or do you have two computers connected to the Internet? If it is the latter, double check that the cable connecting the Ubuntu computer to the modem or router is still properly connected.

Let's collect a little bit of information about what is happening.  I assume you are reading this in Windows. First copy the commands from the box below and paste them into a text file on your Windows system:
```
ifconfig
ping -c 4 192.168.1.1
ping -c 4 64.233.187.99
ping -c 4 google.com
ifconfig
```
Now we need to use that file of commands in Ubuntu (unless you want to type them by hand). If you can access Windows files from Ubuntu, then remember where the text file is so you can find it when you are in Ubuntu. Otherwise, copy the text file to a floppy disk, or a USB Flash drive, or anywhere that you can read it from Ubuntu. Then shutdown Windows and start Ubuntu.

When Ubuntu is running, get that text file, and open it in an editor. Then open the Terminal: Go to the Application menu, choose Accessories, and from there choose Terminal. (This is assuming you are using Ubuntu, rather than one of the variants.)

Now, highlight the commands in the text file, copy them, paste them into the Terminal. You may have to push Enter to get the last command to run. 

Open a new text file in an editor, then copy all of the text from the Terminal window, paste it into that new text file and save it. Be sure to get all of the commands and their output. Copy that new text file onto the floppy or USB Flash drive, or copy it back to the Windows disk -- anything so you use that text from Windows.

Now shutdown Ubuntu, startup Windows, then make a post here into which you paste the text you saved from running those commands on Ubuntu.  Also in Windows, open a Command Prompt window (some call it the DOS prompt). Type the following command:
```
ipconfig /all
```
Copy the result of that command from the Command Prompt window and paste it into the same post with the text from Ubuntu. Also in the post, tell us about how you are connected to the Internet. Is it DSL modem, cable modem, dial-up? Do you have a router between the computer(s) and the modem? Send that post to the forum. 

Copying text from a Command prompt window in Windows is a little odd. You must first click on the little box in the upper left corner of the window and select Edit, then Mark from the menu. Then use the mouse as usual to highlight the text to be copied, then push the Enter key to copy the highlight to the clipboard. You can paste it into the post window the normal way. In case you don't know how to start the Command Prompt, click the Start button, open Programs, then Accessories, and select Command Prompt from there.

We will look at the information in your post and either tell you how to fix the problem, or, more likely, tell you what information to check next.

---

### Post by arvindenrique on 2008-01-09
i have windows and ubuntu on the same computer with an adsl modem

---

### Post by rkd on 2008-01-10
Okay, since Ubuntu is on the same computer, the problem can't be the cable from the computer to the modem.

The other things I asked in post #2 will help narrow down what is going wrong. Post that information when you can.

---

