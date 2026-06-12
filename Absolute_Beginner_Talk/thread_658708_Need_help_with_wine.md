---
title: "Need help with wine"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by Kinrui on 2008-01-04
Im trying to connect my computer to the internet. Problem is, im using an adsl modem and the installation disc contains an .exe file that couldn't be read. After reading up on it in the forums i tried getting wine using synaptics. However, some files need to be downloaded off the net which is impossible since i dont have internet connection in the first place.              
Can anyone provide some explaination please? Would appreciate any help. Thanks.

---

### Post by JoshuaRL on 2008-01-04
I don't have much experience with that, but I think you might be going about this the wrong way.  WINE is a compatability layer that is made to run Windows programs through Linux.  So installing drivers usually don't work that way since you'd have to run WINE every time you needed that driver.  So you would be better off if you could find an open source driver for your modem.  Try searching on the forums and Googling for the exact make and model #.

---

### Post by Kinrui on 2008-01-05
Ok thanks alot. I'll go try it out now.

---

### Post by rkd on 2008-01-05
This might not apply to you -- I don't know where you are located -- but in the U.S., assuming the modem connects via ethernet (not USB), the installation CD that many Internet Service Providers include with the modem really isn't necessary. It usually contains some software to help the ISP's technician when you call for help, sometimes some antivirus software that the ISP sponors, often a bunch of plug-ins for the browser that you probably don't want, and maybe some other generally useless software, but nothing essential for actually using the modem.  

That's the situation with all the cable modems I've seen.  I'm not as familiar with DSL modems. I guess in some cases, the software on the CD with DSL modems includes a program for setting up the PPPoE stuff, which is necessary, but I believe Ubuntu contains a PPPoE setup program, which I assume serves the same purpose.

So you may be able to forget about the CD that came with the modem. Your situation may be different, so if what I say isn't true for you, sorry, I don't mean to mislead you.

Good luck on getting it going!

---

### Post by philinux on 2008-01-05
What's the make and model of the modem?

---

### Post by geirha on 2008-01-05
I agree with rkd, you most likely just need to set up PPPoE [https://help.ubuntu.com/community/ADSLPPPoE?highlight=%28pppoe%29](https://help.ubuntu.com/community/ADSLPPPoE?highlight=%28pppoe%29)

---

### Post by Kinrui on 2008-01-05
> **philinux said:**
> What's the make and model of the modem?

aztech dsl206u

Still working on it. Will try out all the advice you guys gave me after lunch.

Once again, thanks alot!

---

### Post by bwtranch on 2008-01-05
I agree with post 2,3, and 6. You don't need Wine for this one and it won't help you. Unfortunately, I'm not that great with DSL modems, either. Mine is a wieless modem/router. But, it shouldn't be that much different. Can you go to your computer and enter (in a browser)  198.162.2.1 or 198.168.1.1 and see if you can get a config screen? or try and ping the router?

---

### Post by Kinrui on 2008-01-06
I think i need to clarify something.

I have a very very very limited knowledge of computers.

I have a dsl modem that uses USB cables. (Aztech DSL206U)

Is there any way to set up an internet connection?

Sorry for having to make you guys try to explain in such detail but i have no idea what you guys mean.

Thanks for trying to explain. :):)

---

### Post by bwtranch on 2008-01-06
Oh, not a problem. I had a hard time starting out. Some people on this forum still don't like me. Not a problem. 

Do you know how to use the terminal? We can get some output from that and diagnose the problem. If you go to Applications -> Accessories -> Terminal you should see something like this:

jim@jim-desktop:~$ 

Now, that is a CLI or Command Line Interface. It uses something called bash. and that damn bash will make you want to trash it. But, it is your friend. Believe it or not. So, if we can get to your problem, we need to access this. Once you have done this please let me know.

---

### Post by Kinrui on 2008-01-06
Yup, managed to open the terminal. No sweat.

What next?

---

### Post by c0met on 2008-01-06
I have an ADSL modem. I'm not an expert in this stuff, but this is how I understand the system to work.

[LIST]
[*]It is necessary to configure the modem to connect to your ISP
[*]your ISP will provide information on that
[*]this is easiest done by using a web-browser (I used Firefox) to log into your modem and then to perform the necessary set-up procedure
[*]once the modem is set-up, close the web-browser
[*]it's also probably a good idea to reboot Ubuntu (while that might not be needed, it won't hurt)
[*]before you restart Ubuntu, make sure your modem is switched on
[*]open up a web-browser and see if you can connect to (say) google.com
[*]if you can't, right click on the [COLOR="Purple"]**Network Symbol**[/COLOR] (top right side of the screen, near the [COLOR="Purple"]**Close**[/COLOR] symbol)
[*]click on **[COLOR="DarkRed"]Enable Networking[/COLOR]** to deactivate it
[*]now reclick on [COLOR="DarkRed"]**Enable Networking**[/COLOR] to re-activate it (I find that sometimes I have to kick the network into action)
[*]right click on the [COLOR="Purple"]**Network Icon**[/COLOR] once more and now select [COLOR="DarkRed"]**Connection Information**[/COLOR] (you should have ISP numbers and not 0's. If only 0's are present this means that the network connection is not working
[/LIST]

Good luck!

---

### Post by rkd on 2008-01-06
Okay, I understand that your modem connects to the computer via USB rather than ethernet. That makes it more difficult. We do need to get some special software installed.

I saw one web page on which in referred to the Linux directory on the CD that came with the modem. Take a look at the contents of the CD you have to see whether it has a directory named Linux. If it does, look at the files in that directory to see whether there is a README or INSTALL file, or any other file that might tell you something about what is in the directory and how to use it.

Edit: I forgot to say that I think you can look at the contents of the CD either on Linux or on Windows (or on a Mac, for that matter). If you try it on something other than Linux and you don't see a directory named Linux on the CD, do try it on Linux, just to make sure the CD wasn't set up to hide the Linux directory except when viewed from Linux. I doubt they did that (I don't know whether that's even possible), but check it on a Linux system if you don't see the Linux directory on another kind of system.

Meanwhile, I'll look a bit more on the web for advice about how to get your modem working with Linux.  I did see that the page describing the modem on the aztech site does say it is supported in Linux, so there is a good chance they have something to use with Linux on that CD.

---

### Post by Kinrui on 2008-01-06
> **c0met said:**
> [*]this is easiest done by using a web-browser (I used Firefox) to log into your modem and then to perform the necessary set-up procedure


Thanks for the help. But do you mind giving more details for this step?

Thanks for helping too rkd. I viewed the disc on Linux and this is what it contains:

- ADINST16.dll

- ADINST32.dll

- adiusb.inf

- ADIUSB.ico (icon file?)

- Company.ico

-  AUTORUN.inf

- Cleanup.exe

- Data1.cab

- Data1.hdr

- unaddrv.exe

- Data2.cab

- dslgu.ini

- dsltest.ini

- ikernel.ex_

- layout.bin

- setup.inx

- setup.exe

- setup.ini

There is also a folder titled 'Manual' that contains some .gif images and a .pdf file that i presume is not needed.

Btw, what is a directory?

---

### Post by rkd on 2008-01-06
I believe c0met doesn't understand that you have a USB-connected DSL modem. His (or her) suggestions sound to me to be ones suitable only for an ethernet-connected modem.

"directory" is the Linux term for what you call a folder. 

The pdf file on that CD might be the only thing useful to you in the Linux environment. Scan through it to see what kind of information is there.

I found what looks like very good, step-by-step instructions for setting up your modem (and any modem containing the Eagle chipset) in Ubuntu.  It is at:

[https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm](https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm)

It has instructions for Ubuntu 6.06, 6.10, and 7.04. I imagine you are using Ubuntu 7.10. Let's assume the instructions for 7.10 are the same as Ubuntu 7.04 and see how far we get. 

Don't let the length of the instructions worry you -- the steps are small and well-explained. If you take them one at a time, I think you will find them not hard to follow. Notice that since you don't use Ubuntu 6.06, there is a large section from step 6 of "Setting up the modem" to "Configuring The Connection" that you get to skip entirely.

It sounds like you are very new to Linux, so let me give you some tips about things those instructions don't explain. (I'm assuming you are using Ubuntu. If you are using Kubuntu or another of the variants and don't know how to interpret these tips on your system, ask and I'll explain.)

You don't have to type all those commands given in the instructions yourself.  On the computer you use to read that web page, copy the commands from the web browser window and paste them into a text file. Copy enough extra text into the file so it is easy to find your place when looking through the list of commands later. When you have all the commands in that text file, close it and copy it to a USB flash drive, a floppy disk, or burn it to a CD-R or CD-RW -- anything that will let you carry a small file from that computer to your Ubuntu computer. Then carry the file to your Ubuntu computer and copy that text file into any convenient place. Open it in a text editor. You can carry the modem firmware file mentioned in step 1 of the instructions on the same device at the same time.

If the two computers are too far apart to easily look from one to the other, it might be good to print the whole web page so you can easily read the instructions while working at the Ubuntu computer.

In order to carry out the instructions on that web page, you have to use a Terminal window. To do that, Open the Applications menu, choose Accessories, then choose Terminal. When it is time to run one of the commands given in the instructions, use the mouse pointer to select it in the window containing the text file. Selecting text automatically copies it into the clipboard. Then move the mouse pointer to the terminal window and click the scroll wheel (or click both mouse buttons at the same time) to paste the copied text into the Terminal window, then push the Enter key to run the command.  If you have to edit the command, edit it in the text editor window before you copy it.

If you need to save any output from a command to post in a later question in the forum, you can highlight it in the Terminal window with the mouse pointer, then paste it into an editor window. It usually is a good idea to copy the command that produced the output at the same time so we know what command produced the output. When you have gathered all the text you want to save, save the file or close the editor to save it to disk. If the Ubuntu computer still isn't connected to the internet, you can copy the file onto a USB flash drive or floppy disk (or to CD-R or CD-RW if you can't use either of those) to carry it back to the computer connected to the internet.

When the instructions tell you to do a command that begins with sudo, it often will prompt you for your password. (If it has not been very long since the last time it prompted you for your password, it will remember it and skip the prompt.) When you see the prompt, type the same password you use at a normal login. While you are typing the password, nothing will echo, so it might seem as if your typing is being ignored, but it does see the characters you type. When you have typed the password, push Enter. If you entered the password correctly, the command will be performed. If you made a mistake typing the password, it will ask you for the password again. The gksudo command is another form of sudo and the password prompt works the same way.

When you are entering commands, you could do several at once by copying and pasting several lines, but it is better to copy and paste one line at a time so that if there is an error, you can stop and investigate right away. The exception to this is later in the instructions, when it is telling you to create some files with gedit. In that case, you can copy and paste all of the lines that are to go into the file at the same time (and paste them into the gedit window, not the Terminal window).

I think you can skip the part of the instructions following the title "(advanced) Starting automatically with udev". We can go back and do that later if you want to.

Okay, now go read those instructions and see whether they make sense to you. If you feel you understand them well enough to carry out the steps described, go ahead and try them. If you have any questions about what the instructions mean or how to do something it doesn't explain clearly, post your questions here and I or someone else will help you understand. If you run into an error while following the instructions that you don't know how to correct, collect the error message and any other information that seems connected with it, post it here, and we'll try to help.

Good luck!

---

### Post by c0met on 2008-01-06
Hi Kinrui,

You ISP should have given you password/login information. For me, this came in a separate letter. What you need to have are the login name and password for modem (this would be generic; mine was admin/admin, but it would be different for your modem.) Then you would  probably need to have a password for your modem to use to get into your ISP (in my case, this was different from the login password that I use to connect to email, etc).

It might be worthwhile having a hunt around your ISP's website. There is often the necessary information there (although your personal password details won't be there, of course).

---

