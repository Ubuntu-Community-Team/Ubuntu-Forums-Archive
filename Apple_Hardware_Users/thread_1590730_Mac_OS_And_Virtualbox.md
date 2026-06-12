---
title: "Mac OS And Virtualbox"
date: 2010-10-08
forum: Apple Hardware Users
---

### Post by TheMixtureMedia on 2010-10-08
Hey there I was wondering if anyone knows how to install Mac OS X 10.6.3 on virtualbox on Ubuntu 10.10. I have tried but it does not want to install for me any thoughts.

---

### Post by TheMixtureMedia on 2010-10-08
Anyone at all??

---

### Post by samigina on 2010-10-08
[http://lifehacker.com/5583650/run-mac-os-x-in-virtualbox-on-windows](http://lifehacker.com/5583650/run-mac-os-x-in-virtualbox-on-windows)

---

### Post by TheMixtureMedia on 2010-10-08
I did what it told me but when I uncheck Enable EFI the system does not find the cd or iso I have. It comes up for a boot screen like it can not find anything. But when I click the enable efi it comes up but all I get is a grey screen and a spining wheel.

---

### Post by snowpine on 2010-10-08
Apple has chosen not to support this; they want you to buy a Mac. Not really an Ubuntu question/issue.

---

### Post by TheMixtureMedia on 2010-10-08
Then why is it a option on VirtualBox and why would Windows work I do not understand??

---

### Post by TheMixtureMedia on 2010-10-08
There are videos on youtube with people doing this

---

### Post by snowpine on 2010-10-08
I'll be blunt: your question has nothing to do with Ubuntu, and discussion of torrenting/slipstreaming/hackintoshing Mac OS X really belongs on a different forum.

---

### Post by corrytonapple on 2010-10-08
The option is there so MAC users can use OSes higher than the ones included without dedicating space and installing it to the HDD without OS option screens and such. Apple wants you to buy a Mac to run a Mac OS. Snowpine is correct.

---

### Post by MisterGaribaldi on 2010-10-09
It's an arbitrary limitation imposed by Apple. To be fair, Microsoft doesn't like it when you virtualize their OSs (except for a certain range that they will allow).

The difference here is twofold. First, there are far more people working on getting Windows to be "virtualizable". Second, Microsoft doesn't *want* you virtualizing their mainstream OS offerings; Apple *will not tolerate* you virtualizing theirs.

---

### Post by TheMixtureMedia on 2010-10-09
> **snowpine said:**
> I'll be blunt: your question has nothing to do with Ubuntu, and discussion of torrenting/slipstreaming/hackintoshing Mac OS X really belongs on a different forum.

I am not torrenting I own a legal copy of Mac OsX this is a apple forum. So this is why I want to ask about this I do not like how you are talking to me snowpine. If this is the case and it will not work (with a legal copy). Fine I am going to stop talking about it I am sorry.

---

### Post by snowpine on 2010-10-09
> **TheMixtureMedia said:**
> I am not torrenting I own a legal copy of Mac OsX this is a apple forum. So this is why I want to ask about this I do not like how you are talking to me snowpine. If this is the case and it will not work (with a legal copy). Fine I am going to stop talking about it I am sorry.

It was not my intention to make you feel bad. I'm sorry. :)

---

### Post by corrytonapple on 2010-10-09
Yes, it will not work. The only option is to get a mac. The older ones are pretty cheap nowadays.

---

### Post by kaldor on 2010-10-09
This type of discussion is (sadly) not permitted on the forums... don't be surprised if you see this locked soon :(

I believe it is possible to run OS X on VBox inside another OS X host, but not outside. Maybe that's why the menu entry is there?

It's also breaking the Apple EULA by using it on a non-Apple device (silly as it is).


And this question DID have something to do with Ubuntu; running OS X as a guest inside Linux?

---

### Post by Simian Man on 2010-10-09
> **MisterGaribaldi said:**
> It's an arbitrary limitation imposed by Apple. To be fair, Microsoft doesn't like it when you virtualize their OSs (except for a certain range that they will allow).

The difference is that Windows is used in enterprise settings where virtualization is a very useful tool.  OSX is pretty much never used in that way so the only people who'd want to virtualize it are those who are too cheap to buy a Mac :).

---

### Post by zzzakattack on 2010-10-09
I think this heavily has to do with Ubuntu, because it's the operating system being used to run virtualbox, and sometimes that is a key factor in why the client OS isn't running correctly.

I've had this same question before, and I've tried to run mac in virtualbox (I own a legal copy too), on many different OS's, and many different computers with many different specs, hardware, etc.  I've even modded my Mac with multiple mods many times, and used many settings on the virtualbox.

The closest I ever got was running the install screen, but unfortunately after I install, the install medium won't boot.

As of right now, I think it's very possible, but very difficult.  I guess I should rephrase that: As of right now, it is possible to those who are extremely advanced in both Mac and Linux (or windows and Linux), and know how to go into the config text files of virtualbox, to edit options not listed on the gui (even doing that I still failed), and has had many experience with configuring things.  While most people can't do half of this stuff.

But still, the fact that I got close to the install screen, and the fact that it's possible, means that you do have some potential to do it!  Good luck!

---

### Post by MisterGaribaldi on 2010-10-09
The installer does what's called a "gestalt" of the system it's being used on, and also checks for a certain data statement from some custom chip they put on their own systems. When it doesn't get those, it will fail.

It is possible to fake the chip, and it's also possible to hack a copy of Mac OS X not to check, but that's when you're getting clearly into "hacintosh" territory, and I don't know if the folks here on UbuntuForums really like discussing such things. :shock:

---

### Post by slick666 on 2010-11-21
As a side I hate to see tis topic getting flamed everytime I see a discussion coming up. So to answer the questions before they come up.

[LIST]
[*]I own a Macbook
[*]I own OSX 10.4
[*]I own OSX 10.5
[/LIST]

Just because I want to run OSX in Virtualbox does not mean I'm doing anything illegal or immoral. As far as I can tell it's not illegal to run OSX virtualized or no on mac hardware. I'm not here to talk about legal or ethical questions, just technical. 

I can run Ubuntu in a VM but I want to run OSX in a vm now. I don't see why I can't do this. Right now the 10.5 DVD boots up just fine but it seems to hang when trying to start the installer. I have some original 10.4 install CDs but they seem to boot jut up into a shell. I'm guessing that the install is hanging from some technical issue not that it's failing the hardware test. If anyone has gotten past this any info would be helpful.

---

### Post by snowpine on 2010-11-22
> **slick666 said:**
> As a side I hate to see tis topic getting flamed everytime I see a discussion coming up. 

If you don't want to get flamed, please post your question on the appropriate forum. Ubuntu Forums is not the venue to discuss circumventing Apple's EULA (whether or not you personally agree with it).

---

### Post by Joeb454 on 2010-11-22
Running OS X on a virtual machine (other than those designed for OS X itself) is in breach of Apples EULA, thus prohibited from discussion on this forum, as it's something we don't support.

If you are interested in running a virtualised instance of OS X, you would need to run OS X server, as this is the only edition that Apple allow to run in a virtual environment (the latest edition of VirtualBox supports this as a guest OS, for example).

---

### Post by slick666 on 2010-11-22
> If you don't want to get flamed, please post your question on the appropriate forum. Ubuntu Forums is not the venue to discuss circumventing Apple's EULA (whether or not you personally agree with it). 

Sigh this is an apple user asking a question in an apple user forums I don't believe there is a better forums in ubuntu forums. I'm not discussing circumventing Apple End User Software License Agreement. Period.

> Running OS X on a virtual machine (other than those designed for OS X itself) is in breach of Apples EULA, thus prohibited from discussion on this forum, as it's something we don't support.

No that is **not** true. I don't believe I violate the End User Software License Agreement. I can run OSX under a VM and I believe the excerpt below supports me.

> Single Use. This License allows you to install, use and run one (1) copy of the Apple Software on a single Apple-labeled computer at a time


Just like Windows license only allows a user to run one copy per license at a time OSX is the same way. Despite the fact that users may run more than one copy of windows and therefor may violate Windows EULA does not prohibit it from open discussion. I believe that in the same way that just because I "may" violate the EUSLA of OSX it does not prohibit from open discussion in the forums. If I run an OS in a VM (Windows, OSX, or otherwise) there are certain limitations based on the license, but the threat of me violating those licenses does not bar it from being discussed. you can see evidence of this in any thread talking about putting windows in a VM. I understand that the EUSLA of OSX does limit you to executing the machine on APPLE labeled hardware. I have clearly stated that I have purchased the hardware, the software, and have never suggested executing OSX on anything else. I believe that I fully comply with both the legal description and the spirit of the EUSLA.

I'm not here to discuss legal matters I'm here to discuss technical ones. I see no reason why my discussion should be stifled.

---

### Post by Joeb454 on 2010-11-22
I'd never noticed that part of the EULA before, however, provided your hardware is indeed Apple hardware, I can't see this being too much of an issue based on that excerpt.

That said, I am not a lawyer, so don't take my word for this.

---

### Post by snowpine on 2010-11-22
The short answer to your question: Apple does not officially support OS X in VirtualBox. Oracle does not officially support Mac OS X in VirtualBox. Make friends at both companies. Get them to sit down together and make a deal.

Long answer: Google "hackintosh" and you will have your answer. :)

---

### Post by cprofitt on 2010-11-26
> **snowpine said:**
> If you don't want to get flamed, please post  your question on the appropriate forum. Ubuntu Forums is not the venue  to discuss circumventing Apple's EULA (whether or not you personally  agree with it).

You may want to check your facts snowpine ... you seem to have ignored  some very important details that render your argument invalid and you  are bordering on being disrespectful.

> **snowpine said:**
> I'll be blunt: your question has nothing to do  with Ubuntu, and discussion of torrenting/slipstreaming/hackintoshing  Mac OS X really belongs on a different forum.
 
 I do not believe the original poster specified their hardware platform  so you may or may not be correct. Ubuntu can run on Apple hardware so it  is entirely possible that they want to run Ubuntu as their main OS with  OS X in a Virtualbox. One should clarify before making assumptions that  reflect poorly on a posters character. You owe them that much respect I  would think.
 
 
 > **TheMixtureMedia said:**
> Hey there I was wondering if anyone knows  how to install Mac OS X 10.6.3 on virtualbox on Ubuntu 10.10. I have  tried but it does not want to install for me any thoughts.
  
  I believe the issue is that currently the only version that supports  virtualization is OS X server. Though it has been a while since I  checked.

---

### Post by snowpine on 2010-11-26
> **cprofitt said:**
> You may want to check your facts snowpine ... you seem to have ignored  some very important details that render your argument invalid and you  are bordering on being disrespectful.

 I do not believe the original poster specified their hardware platform  so you may or may not be correct. Ubuntu can run on Apple hardware so it  is entirely possible that they want to run Ubuntu as their main OS with  OS X in a Virtualbox. One should clarify before making assumptions that  reflect poorly on a posters character. You owe them that much respect I  would think.

The OP's method for installing OSX in VirtualBox (link in post #3) requires downloading a "cracked" version of OSX from a questionable website:

> The group Hazard has put out a good patched Snow Leopard installer that should do fine (just search for it on Google). Of course, if you feel bad about downloading the ISO of Snow Leopard, you could always go buy a copy to feel a bit better, karmically.

If such piracy is, indeed, considered appropriate and on-topic for Ubuntu Forums (I am not a moderator so I'm unclear on the rules), then I retract my criticism and apologize to anyone I may have offended.

---

### Post by untmdsprt on 2010-11-28
I've just tried installing the retail version of Snow Leopard and yes it does work, but it has some issues. Here is what I have and maybe someone can confirm a different way to do it.

My Macbook is a mid-2007 2.16GHz Core 2 Duo with 2GB RAM. Currently running v10.6.5 Mac OS in 32bit mode. Apple decided not to allow this computer to run in 64bit mode although most programs will do so.

For testing purposes I ran Virtualbox in OS X and created a Mac 32bit virtual client. Had to format the "drive" first then installed OSX. After it finished and restarted it did a verbose listing of everything the computer was doing instead of the familiar Apple logo. When it finished, everything looked and acted like the normal Mac computer. Shutting down the computer also gave the verbose listing of what it was doing.

Going into the "About this Mac" window, I did get "Intel Core 2 Solo" instead of Duo. I'm not for sure if using the 64bit Ubuntu would actually be better in getting a 64bit Mac client in Virtualbox. Maybe someone else can confirm this.

---

### Post by slick666 on 2010-12-01
I've had some issues installing the 10.4 and 10.5 CDs in Virtualbox directly. There could be some hang ups there that people aren't looking into because the OSes are old. I was able to get 10.5 to run under virtualbox by doing the following.

[LIST=1]
[*]Install OSX completely on my Macbook wiping everything
[*]DD'ing the Hard drive to an external image
[*]creating the .vdi file using Virtualbox tools
[/LIST]

I put a 10.10 live CD in and was able to create and execute the .vdi on the external hard drive in a virtual machine with no problems. Now that I know I can do it this way I'm going out and buying 10.6 and am going to create my final .vdi file from it before installing ubuntu on My MacBook. I going to also try creating a VM the normal way after untmdsprt claimed that it installed fine for him. It could just be an issue with the installer environment with 10.4 and 10.5. 

One side effect I noticed that when I created a compressed .vdi file of the DD image is that all the space was detected as allocated. According the OSX only 18 GBytes is used but the .vdi was the same size as the DD. I'm guessing that since the file system is HFS+ the VBox utility sees it as all being used. If I'm going to create the virtualmachine from my Laptop I'm going to have to partition it in the size that I want the virtual machine to be.

---

### Post by slick666 on 2010-12-17
I took the plunge and bought 10.6 and it installed right in VirtualBox for me. I had a hangup about my keyboard which caused me to restart but it picked up and continued the install no problem. I've only had it up for a day but I should be able to get back to it this weekend and finish it up.

---

### Post by alexthunder on 2011-01-26
[http://lifehacker.com/5583650/run-mac-os-x-in-virtualbox-on-windows](http://lifehacker.com/5583650/run-mac-os-x-in-virtualbox-on-windows)

---

### Post by snowpine on 2011-01-26
> **alexthunder said:**
> [http://lifehacker.com/5583650/run-mac-os-x-in-virtualbox-on-windows](http://lifehacker.com/5583650/run-mac-os-x-in-virtualbox-on-windows)

> Apart from VirtualBox, you'll also need an OSX86 ISO. The group Hazard has put out a good patched Snow Leopard installer that should do fine (just search for it on Google). Of course, if you feel bad about downloading the ISO of Snow Leopard, you could always go buy a copy to feel a bit better, karmically.

:(

---

### Post by Raditude on 2011-01-29
My school is sending my MacBook this weekend. Once I get it, I'm wiping it, and installing Ubuntu. Then inside of Ubuntu, I will install OSX as a guest, from the backup disc they give me. Here's the tutorial I'll be following:

[http://www.taranfx.com/install-snow-leopard-virtualbox](http://www.taranfx.com/install-snow-leopard-virtualbox)

---

