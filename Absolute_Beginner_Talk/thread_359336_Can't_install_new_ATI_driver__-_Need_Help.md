---
title: "Can't install new ATI driver  - Need Help"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-02-11
My computer keeps crashing because I have an unsupported video driver. I've downloaded a new driver for my ATI Radeon 9200SE. It is a "run" install. When I dbl-click, it starts to install then tells me that it can't find the file /home/kittyhawk63/
What do I do? Why can't it find /home/kittyhawk63/ to install the driver?
I have never manually or otherwise installed a file into Ubuntu. I know only how to install files into Windows. Thanks for any assistance.
BTW, I tried the "The other option you have is to try using envy - http://albertomilone.com/nvidia_scripts1.html" of Jussi01 and it did not work for me. :confused:

:)

---

### Post by dasunst3r on 2007-02-11
Here's an article that I go to all the time: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

If you are going to install manually, you can safely replace "module-assistant" with "m-a" -- save you many keystrokes! ;)

---

### Post by nickoli_02 on 2007-02-11
Use this guide for installing the fglrx driver for ATI cards in Edgy Eft:

[http://www.ubuntuforums.org/showthread.php?t=291464&highlight=fglrx+edgy]("http://www.ubuntuforums.org/showthread.php?t=291464&highlight=fglrx+edgy")

The first part is for installing fglrx, the rest is for other eye candy.

You're right, in unix, / is denoted as the root file directory. /home/kittyhawk63/ is your user's home folder.

---

### Post by kittyhawk63 on 2007-02-11
Why couldn't it find /home/kittyhawk63/ when I dbl-clicked the run file to install? Can these run files be installed from Windows using EXT3?

---

### Post by dasunst3r on 2007-02-12
Are you getting an explicit error saying your file is not found, or does it do nothing when you double-click on it?

As for your 2nd question, the answer is no -- here's why: EXT3 is a file system, not a program.  You will not be able to read your Linux partition from Windows.  Also, the installer has things to do to your Linux installation in order to make the driver work.  Therefore, you can't run the .run file from Windows.

Did the instruction guides help?

---

### Post by Jussi01 on 2007-02-12
> **kittyhawk63 said:**
> I've downloaded a new driver for my Radeon 9200SE. It is a "run" install. When I dbl-click, it starts to install then tells me that it can't find the file /home/kittyhawk63/
What do I do? I have never installed a file into Ubuntu. I know only how to install files into Windows. What is  /home.kittyhawk63/  ? Is the "/" telling me a root directory? Thanks for any assistance.
 
The other option you have is to try using envy - [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

it will setup your card automatically...

---

### Post by Maestro23 on 2007-02-12
.

---

### Post by kittyhawk63 on 2007-02-12
> **Jussi01 said:**
> The other option you have is to try using envy - [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

it will setup your card automatically...

Thanks for this link. I've used it and will see how it works. ):P

---

### Post by kittyhawk63 on 2007-02-12
The link did not help. Still having trouble. Still need to know how to install a "run" file into Ubuntu. See original post to understand my problem. Thanks.

---

### Post by Maestro23 on 2007-02-12
Strange that Envy didn't work.  

Where did you d/l the driver file from? Link please.

---

### Post by kittyhawk63 on 2007-02-12
I'm sorry, I don't remember. It was a link that someone gave me. I aksed him to send it again, but he must be busy with other things in life at this moment. He gave me the link yesterday. I tried checking my posts but could not find that particular post that gave the link. Can I post you privately?

---

### Post by kittyhawk63 on 2007-02-12
I can't find the link. I lost it. I've posted the person that gave it, but he must be off line. He gave it to me yesterday. Can you answer how I can install a run file if it does not recognize where to install the file?

---

### Post by Repent on 2007-02-12
Go to this page and follow their instructions [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717) I had the same thing happen to me and this worked, it's easy and fast.

Hope this helps.

---

### Post by kittyhawk63 on 2007-02-12
Ok! Sorry I couldn't get back sooner. My computer crashed again because of the wrong video driver. I am presently using Windows. I will restart Ubuntu and follow your link. Thanks

---

### Post by kittyhawk63 on 2007-02-12
I checked the link. I don't have a Nvidia card. It is an ATI.

---

### Post by kittyhawk63 on 2007-02-12
I tried Envy. It did not work for me.

---

### Post by Jussi01 on 2007-02-12
What was the problem with envy? what error did it give you?

---

### Post by Repent on 2007-02-12
Check it again Since version 0.8.1 Envy now installs Ati drivers as well as Nvidia.

---

### Post by kittyhawk63 on 2007-02-12
[QUOTE=dasunst3r;2144508]Are you getting an explicit error saying your file is not found, or does it do nothing when you double-click on it?

Yes, it says clearly that it can not find /home/kittyhawk63.

---

### Post by kittyhawk63 on 2007-02-12
I've been needing help on knowing how to install a file into Ubuntu. No one has yet answered the question. See the original for the problem I am having. Thanks.

---

### Post by kittyhawk63 on 2007-02-12
I am so new to writing posts that I think I am running two links without knowing it. Sorry if it takes time to get back to your questions or inquiries.
I tried Envy. It said it was a successful install. But my computer still keeps crashing. I am using windows to keep up this conversation. I need a driver that takes care of the problem in Ubuntu. I have downloaded the driver but am having one big time trying to figure out how to install it. It is a run file. No one has offered a suggestion (as of yet) that has helped me. Still taking offers.

---

### Post by Repent on 2007-02-12
> I tried Envy. It did not work for me. I understand what you are saying I to was unable to use Envy the way the other have told you to do, But this installs it in a different way "IT WORKS". What do you have to lose give it a try.

---

### Post by kittyhawk63 on 2007-02-12
> **Repent said:**
> I understand what you are saying I to was unable to use Envy the way the other have told you to do, But this installs it in a different way "IT WORKS". What do you have to lose give it a try.

Repent
What are you referring to when you say, "IT WORKS"? Is it other than Envy?

---

### Post by Jussi01 on 2007-02-12
> **kittyhawk63 said:**
> I am so new to writing posts that I think I am running two links without knowing it. Sorry if it takes time to get back to your questions or inquiries.
I tried Envy. It said it was a successful install. But my computer still keeps crashing. I am using windows to keep up this conversation. I need a driver that takes care of the problem in Ubuntu. I have downloaded the driver but am having one big time trying to figure out how to install it. It is a run file. No one has offered a suggestion (as of yet) that has helped me. Still taking offers.


Ok, Im sorry to harp on about envy, but i know it has worked for many people. Did you follow the instructions after the installing envy?

 1) Download and install the deb package

2) Log out and press CTRL+ALT+F1 (so as to get out of the Desktop Environment, i.e. you'll see ONLY the command line)

3) Log in (if required)

4) Run "envy" by opening Terminal or Konsole and typing (quite obviously):
```

envy
```

5) Choose to install or uninstall the driver (from the textual interface)

If you havent done all this (i suspect you only installed the deb) then please try this...

Cheers


Jussi

---

### Post by kittyhawk63 on 2007-02-12
[QUOTE=Jussi01;2145564]Ok, Im sorry to harp on about envy, but i know it has worked for many people. Did you follow the instructions after the installing envy?

 You are so right. I am so new to this "Do it this way" over "Easy install .exe files"  through Windows that I overlooked the rest of the install. Thanks for this correction on my part. I will print it out and follow it to the letter.

---

### Post by Repent on 2007-02-12
No its Envy, it just installs it so it works, like I said I tried every thing all the others said to do to get Envy to work.  But only the info on the page I gave you worked and it states right on the website it supports ATI drivers. Try it please.

---

### Post by Jussi01 on 2007-02-12
;) No problems mate. good luck with it.

---

### Post by kittyhawk63 on 2007-02-12
> **Repent said:**
> No its Envy it just installs it so it works, like I said I tried every thing all the others said to do to get Envy to work  But only the info on the page I gave you worked and it state right on the website it supports ATI drivers. Try it please.

Repent,
I'm on my way to rebooting and using Envy again. I'm using WinXP at the moment. Thanks everyone for the help.

---

### Post by Maestro23 on 2007-02-12
> **kittyhawk63 said:**
> [QUOTE=Jussi01;2145564]Ok, Im sorry to harp on about envy, but i know it has worked for many people. Did you follow the instructions after the installing envy?

 You are so right. [COLOR="Red"]I am so new to this "Do it this way" over "Easy install .exe files"  through Windows that I overlooked the rest of the install.[/COLOR] Thanks for this correction on my part. I will print it out and follow it to the letter.

You must "unlearn" what you learned on the other side of the fence.;) 

Good luck.

---

### Post by kittyhawk63 on 2007-02-12
I was able to follow your instructions for properly installing the Envy files. Everything seems to be working fine at this moment. I appreciate all the help that evryone has given. I have learned much today. Thanks for the link to Envy. Thanks for the easy to follow instructions to get Envy to download the needed files. I will now close this thread when I am told how to do it.
Thanks again.
kittyhawk63

---

### Post by kittyhawk63 on 2007-02-12
Do not need to answer this last question. I will leave it for other to get some help. Thanks.

---

### Post by Repent on 2007-02-12
Did you use my link?

---

### Post by Jussi01 on 2007-02-12
Go to your original post, click edit, click go advanced, then click the checkbox for this thread is resolved. then save. :D

---

### Post by kittyhawk63 on 2007-02-12
> **Repent said:**
> Did you use my link?

Yes, everything is working great. Thank you.

---

### Post by kittyhawk63 on 2007-02-12
> **Jussi01 said:**
> Go to your original post, click edit, click go advanced, then click the checkbox for this thread is resolved. then save. :D

Thanks for this info.

---

### Post by Repent on 2007-02-12
You're welcome I'm glad I could help, I would bookmark that page just encase.

---

### Post by zeca_pedra on 2007-08-02
> **kittyhawk63 said:**
> My computer keeps crashing because I have an unsupported video driver. I've downloaded a new driver for my ATI Radeon 9200SE. It is a "run" install. When I dbl-click, it starts to install then tells me that it can't find the file /home/kittyhawk63/
What do I do? Why can't it find /home/kittyhawk63/ to install the driver?
I have never manually or otherwise installed a file into Ubuntu. I know only how to install files into Windows. Thanks for any assistance.
BTW, I tried the "The other option you have is to try using envy - http://albertomilone.com/nvidia_scripts1.html" of Jussi01 and it did not work for me. :confused:

:)

double clicking doesn't work. In linux distros I've learn that run files are just another form of scripts so you have to work with them from terminal (or console). That said, check in your applications menu for terminal and do as follows:

1) open terminal
2) su
3) your root password
4) sh ati-the-rest-of-the-name-of-the-file.run
5) follow installer instructions

hope this helps,
zeca

UPDATE: sorry, I answer the fast I could without reading these last posts. Glad to know that with Envy everything worked. You can ignore this (I delete it if I knew how) :-p

---

