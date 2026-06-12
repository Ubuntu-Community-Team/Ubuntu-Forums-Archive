---
title: "SAMBA problem"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-02-04
I'm trying to share files between my Linux computer and the other Win XP computer securely so I'm following this Tutorial
**How to share files using Samba (the more secure way)**
[http://ubuntuforums.org/showthread.php?t=26438](http://ubuntuforums.org/showthread.php?t=26438)

But I'm all confused regarding what this part means for me?
> Finally, create a SMB user, make sure this account exists on your Ubuntu Linux.
[QUOTE]sudo smbpasswd -a `whoami`[/QUOTE]A SMB user should that be the same as my regular login name?
##----------------------------------------------------------
Also [network user] should that be exactly the same as "whoami".  Or which part of my regular Linux login info should I put in there?  For example my name is "Taco" and my hostname is Bell so in terminal it looks like this 
> Taco@Bell:~  Should [network user]= Taco or Bell :confused: 
This home networking sure is troublesome!
> 
------------------------------------------------------------------------------------------------
Linux
------------------------------------------------------------------------------------------------
Install smbfs:
```
sudo apt-get install smbfs
mkdir Network
sudo mount -t smbfs -o username=[[COLOR="Red"]network user[/COLOR]],password=[network pass],uid=`whoami`,gid=`[COLOR="Red"]whoami[/COLOR]`,fmask=000,dmask=000  //[whatever you named the Samba server]/[network user] /home/`whoami`/Network
```

Example:
```
sudo mount -t smbfs -o username=[COLOR="Red"]kenny[/COLOR],password=test,uid=`[COLOR="Red"]whoami[/COLOR]`,gid=`whoami`,fmask=000,dmask=000  //kenny_smb_server/kenny /home/`whoami`/Network
```
##----------------------------------------------------------

Another question when following that so called secured tutorial the end result will that be like me opening up my ENTIRE home/ folder for the whole world to see?
Shouldn't it be that you only share a certain folder that you select and not your entire personal Home/ folder?

##

---

### Post by Paerez on 2007-02-04
When the person wrote the tutorial, they put in `whoami` instead of the user name of the user because in the terminal `command` will run that command and replace that with the output of the command.

See the difference by running these two:
```
echo whoami
echo `whoami`
```

So that line is setting the smb password for YOU by replacing `whoami` with Taco for you.

Taco@Bell ! haha nice. My name is nick, and my terminal is nick@nite :D

---

### Post by Spano on 2007-02-04
I like th@ idea.  Clever.

---

### Post by jingo811 on 2007-02-04
So what do I put in for [[COLOR="Red"]network user[/COLOR]]?
Would that be Taco as well :confused:
Also that line lewinsky:
```
sudo mount -t smbfs -o username=[[COLOR="Red"]network user[/COLOR]],password=[network pass],uid=`whoami`,gid=`whoami`,fmask=000,dmask=000  //[whatever you named the Samba server]/[network user] /home/`whoami`/Network
```
Do I have to type her in everytime I wanna share my entire /Home folder? (still not by choice)

---

### Post by Spano on 2007-02-04
Taco

---

### Post by jingo811 on 2007-02-04
> 8096: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed
How can i find my mistake or problem?

---

### Post by Spano on 2007-02-04
I know that tutorial can be confusing, this might help.  Here is the command I use to samba into my windows box:
```
sudo mount //dimension4100/F /home/daniel/LAN -o username=daniel,password=cornhole,dmask=777,fmask=777
```
dimension4100 is the windows computer, "F" is the letter of the drive I gave share permissions to in windows.  "LAN" is the folder I created in my Linux home folder to mount the "F" drive to.

You can take a command like that and turn it into a script so you don't have to type it everytime.

Since your passwording these shares and behind a hardware firewall on your LAN I don't think anyone can see your samba shares but you.

You can specify what you share in your /etc/samba/smb.conf

you can see what samba shares are available on your windows machine and how they are named by
typing - smbclient -L "computer IP" into your terminal.  For example
```
smbclient -L 10.0.0.3
```

---

### Post by jingo811 on 2007-02-05
Now I'm really confused :confused: 
**1.)**
I have two PCs at home (PC_1=Ubuntu) and (PC_2=Windows XP).  If I understand the situation right the tutorial I've been following is about turning PC_1 into a server.  The `whoami` and network password stuff was for PC_1 which is the one who's gonna share stuff on the home network.

**2.)**
(PC_2=Windows) in your case a dimension4100 has to share its selected harddrive the F:\ drive in order to access my theoretical (PC_1=Ubuntu) shared folder?

**3.)**
The command line you gave me does that describe a situation where PC_1=Ubuntu shares its folder to PC_2=Windows or the other way around :confused: 
```
sudo mount //dimension4100/F /home/daniel/LAN -o username=daniel,password=cornhole,dmask=777,fmask=777
```

**4.)**
Isn't there a GUI type program for Sharing files in your home network using SAMBA protocol?
All this sounds like stuff aimed at really technical pros and I'm no pro!

---

### Post by jingo811 on 2007-02-10
[COLOR="Red"]Fresh start Bump 1![/COLOR]

OK I need to begin from the top again this SAMBA stuff isn't working for me correctly :( 
> 
Make sure "security" is set to "user".

Scroll down until you see "[homes]", set:
Code:

```
browseable = yes writable = yes
```

Then save the changes.
From the beginning I never set  writable=yes I set it to NO because I don't want my shares to be edited.  Will this little rebellion have screwed up my SAMBA install when following the tutorial?
**How to share files using Samba (the more secure way)**
[http://ubuntuforums.org/showthread.php?t=26438](http://ubuntuforums.org/showthread.php?t=26438)

Also I need to backtrack what I did days ago since this problem have lay dorment for so long.  How can I confirm these inputs?
[network user]
[network pass]
[Samba server]
/Network

I've forgotten most of them, and need some reminders!

---

### Post by bigken on 2007-02-10
sudo aptitude install samba

sudo smbpasswd -e (your name)

sudo smbpasswd -a (your name )

right click files you want to share :)

---

### Post by jingo811 on 2007-02-10
Yeah I did that solution some month ago and it worked again I think, can't confirm it though.
Because I can't use my other PC with Windows XP to find my Ubuntu shares.  Don't exactly know how to make it work in XP.  Never could make any share between XP and XP before so....

I guess I'll just should be satisfied with sharing between Ubuntu and Ubuntu, but my other PC is having Desktop malfunction by random so I can't yet test this SAMBA solution....

Also with the given SAMBA solution how can I password protect my shares this way?
And how can I make it so that only certain PCs have access to my shares without going through that lengthy Tutorial I posted before?

---

### Post by bigken on 2007-02-10
in windows all you need to do is run the network wizzard do have a firewall in windows ?

---

### Post by jingo811 on 2007-02-10
Ah network wizzard that's the trick.  Well now I manage to see my Ubuntu shares however I'm not authorized to access it and from the looks of things my old SAMBA-secure-way settings and yours SAMBA-simple-way are conflicting with eachother or something.

So I still need to fix the secure SAMBA tutorial problems I've encountered!

---

### Post by bigken on 2007-02-10
dont know how but if u can undo the samba config file u created ?

---

### Post by jingo811 on 2007-02-12
Well lets start with the easy stuff first, how can I uninstall SAMBA-the-easy-way that you have suggested?  

Then I'm gonna try get the SAMBA-the-secure-way ppl to help me uninstall their instructions so that my system is completely free from all SAMBA methods.
And begin from scratch again later on....

---

### Post by kidders on 2007-02-12
> Please, need help with Samba.
Could you please come in here and help me troubleshoot my SAMBA?
[http://www.ubuntuforums.org/showthread.php?t=353271](http://www.ubuntuforums.org/showthread.php?t=353271)

Happy to help. The guys here are doing a great job though!

If I were you, I would:

[LIST=1]
[*]Stop samba. (Reinstalling it wouldn't accomplish very much.)
[*]Take a look at smb.conf to make sure it's reasonable looking.
[*]Make sure the rest of my networking is alive (ie that all your machines can talk to eachother).
[*]Restart samba.
[*]Try to access Ubuntu's samba from Windows by "running" **\\the.ip.addr.ess**, and watch it try (and fail) to authenticate.
[/LIST]

Assuming you get this far, you'll need to let remote users access your system. The most straightforward thing to do (samba lets you do all kinds of weird things) is to make samba's usernames/passwords the same as Ubuntu's. You can do that with **smbpasswd**. Authentication should suddenly spring into action for you.

Next up, you would set all your computers to belong to the same workgroup, configure a local master browser, and sort out your naming service, so (a) you don't have to refer to things by number any more, and (b) shares show up in the UIs on your computers.

**One little note**
> Another question when following that so called secured tutorial the end result will that be like me opening up my ENTIRE home/ folder for the whole world to see?User-specific shares are "convenience" shares, and are not intended to be used by anyone other than the user himself. Disabling write access would be ... well ... annoying! If you don't want to use them, you don't have to though. Their usual purpose is to work in tandem with roaming profiles to centralise filestorage on a Windoze domain.

Does any of this help?

---

### Post by jingo811 on 2007-02-13
Tnx for dropping in kidders!
Well suggestion 5 solved things!  I skipped the rest and only did the last step because I didn't know how to accomplish those other steps :-k, Anyhow I can share music between both computers and I no longer need to use my USB stick to transport and exchange error logs everytime I encounter problems on my parents PC.

However being the pedantic axe murderer that I am 8-[ I want to fix these cosmetic trivialities shown on the Windows network GUI.
**1.) Easy SAMBA server - and - Advanced Secure SAMBA server **
seems to have tangled themselves into eachother causing confusion I would guess.
[http://i5.tinypic.com/4dgawbp.jpg](http://i5.tinypic.com/4dgawbp.jpg)
This is what happens when I double click the icon
[http://i5.tinypic.com/2zfin1f.jpg](http://i5.tinypic.com/2zfin1f.jpg)

How should I solve this?  With Easy SAMBA sharing is quick and easy but it doesn't have the security managing features like doing the Secure SAMBA tutorial.  Can they co-exist?
Which should I un-install?

**2.) Renaming Host description**
In Ubuntu sharing settings Host description says this
```
%h server (Samba, Ubuntu)
```
[http://i15.tinypic.com/2u88q6q.jpg](http://i15.tinypic.com/2u88q6q.jpg)
How much of it can I delete and rename, is it like VERY important to keep [%h] or should I leave [%h server] alone and only rename stuff inside the (brackets?)

---

### Post by kidders on 2007-02-14
> **jingo811 said:**
> Well suggestion 5 solved things!  I skipped the rest and only did the last step because I didn't know how to accomplish those other stepsIt's a good idea to be familiar with how samba works before using it. In any case, if you were able to jump straight to step 5, your samba is working. :-)

> **jingo811 said:**
> Easy SAMBA server - and - Advanced Secure SAMBA server seems to have tangled themselves into eachother causing confusion I would guess.What's the difference between the "easy" and "secure" samba setup? I took a quick look at the HOWTO you mentioned in your o/p ... I can't say there's anything particularly *secure* about it, really. :confused:

The problems you're having seem to be largely naming related. Afaik the solution is to get your WINS working properly. If it were me, I would:

[LIST]
[*]Make sure all my computers are part of the same workgroup.
[*]Fiddle my samba configuration so my Linux box is the local master.
[*]Put Ubuntu in charge of WINS.
[/LIST]

For me, getting these cosmetic details right always takes a little experimentation. (Microsoft's filesharing protocols are a little odd!) Samba's logs can be quite informative, when you're wondering what it's up to.

One other thing worth mentioning is that Windows often falls back on DNS when other naming systems don't tell it what it wants to know. Can you ping your Ubuntu box from your Windows box by name?

> **jingo811 said:**
> How much of it can I delete and rename, is it like VERY important to keep [%h]You can call a machine whatever you want. :-)

---

### Post by jingo811 on 2007-02-14
> What's the difference between the "easy" and "secure" samba setup? I took a quick look at the HOWTO you mentioned in your o/p ... I can't say there's anything particularly secure about it, really. 
Well I guess the "easy" SAMBA setup/install is all about GUI which means there's no buttons for adding clients that I want to share to.  
On the other hand what I see as the "secure" SAMBA setup/install you can configurate a bunch of functions by typing in terminal and editing the file that Ubuntu Wiki suggests
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service)

What I meant is if I didn't follow that SAMBA "secure" tutorial I wouldn't be able to activate the security functions in that config file, just by doing it the GUI way right? 	#-o (confusing, I don't know how to explain)

Maybe I should ignore that first "secure" SAMBA tutorial altogether and just follow the Ubuntu Wiki Tutorial instead.  The first tutorial just seemed so quick and easy compared to Wiki, but I guess there are no shortcuts to knowledge.

> 
[LIST]
[*]Fiddle my samba configuration so my Linux box is the local master.
[*]Put Ubuntu in charge of WINS.
[*]Samba's logs can be quite informative, when you're wondering what it's up to.
[*]Can you ping your Ubuntu box from your Windows box by name?
[/LIST]
How do I accomplish that more exactly?  I'm not very knowledgable when it comes to networking stuff.

> You can call a machine whatever you want. 
So erasing ```
%h
``` won't cause problems for SAMBA?

---

### Post by kidders on 2007-02-15
> **jingo811 said:**
> Well I guess the "easy" SAMBA setup/install is all about GUI which means there's no buttons for adding clients that I want to share to. On the other hand what I see as the "secure" SAMBA setup/install you can configurate a bunch of functions by typing in terminal and editing the file that Ubuntu Wiki suggestsAh I see. Many of the posts in this thread describe things in terms of terminal commands and smb.conf settings, which is smart, because they're very unambiguous, and work the same way on everyone's PC, no matter what applications they use. Personally, I would feel much more comfortable configuring something like samba that way, because you always know exactly what's going on. If I were you, particularly since you seem interested in some of the technical little details of how samba behaves, I would stick to that approach. If, however, you come across a nice little graphical administration app that can do what you want, the way you want it done, then there's no reason not to play around with it. :-)

> **jingo811 said:**
> I'm not very knowledgable when it comes to networking stuff.If you'd like to find out more about what samba can do, you should take a look at its documentation. It can be a little flaky in places, but you will certainly be able to find out how to handle things like access privileges, etc.

> **jingo811 said:**
> So erasing ```
%h
``` won't cause problems for SAMBA?Nope. That variable is there simply as a demonstration of how samba can use information from its working environment to control operation.

> **jingo811 said:**
> How do I accomplish that more exactly?Unfortunately, getting some of the cosmetic issues (like smooth operation in graphical environments like KDE & Windows) could be very time-consuming to get through, step by step. I guess the first question is what kind of DNS service you're running, and whether you can ping the computers on your LAN by name.

---

### Post by jingo811 on 2007-02-15
> I guess the first question is what kind of DNS service you're running, and whether you can ping the computers on your LAN by name.
How can I check those things?  I need some specific to-do-pointers.

---

### Post by kosmic on 2007-02-16
I only saw your post now, i've been in germany working :), it is already solved ??

---

### Post by jingo811 on 2007-02-16
It's sort of solved.  I can share files between my PC and my parents PC well.  But I wanted to do that without having to type in the ip all the time, instead I wanted to be able to click it in Windows Networking GUI.  So at this point I just need help optimizing and configurating SAMBA.
> **kidders wrote:**
The problems you're having seem to be largely naming related. Afaik the solution is to get your WINS working properly.

For instance how do I do the below steps, I need 1,2,3-instructions to be able to configurate those.  I don't know much about networking stuff.
> **kidders wrote:**
    * Fiddle my samba configuration so my Linux box is the local master.
    * Put Ubuntu in charge of WINS.
    * Samba's logs can be quite informative, when you're wondering what it's up to.
    * Can you ping your Ubuntu box from your Windows box by name?

---

### Post by jingo811 on 2007-02-20
bump 1.
How do I do the above 4 points?

---

### Post by Carchidi on 2007-02-25
I have three computers running three different OSs: OpenBSD, Ubuntu and W2K3 Server.

The OpenBSD computer uses Samba Server to offer ~/ as a share. I can access this share
from the W2K3 computer just fine, but not from my Ubuntu computer. My Ubuntu computer can access shares offered by the W2K3 computer just fine.

The OpenBSD Samba Server is configured to encrypt passwords and W2K3 Server likes
this. Is there something I must do to Ubuntu to make its Samba Client encrypt passwords?

I am not using Samba Server on the Ubuntu computer; just using the "Connect to Server"
menu entry in the Nautilus Flle Browser. I assume that Samba Client is there in the
background and may need configuration changes; how do I configure it?

---

