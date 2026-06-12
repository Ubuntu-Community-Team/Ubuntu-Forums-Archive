---
title: "Love Ubuntu so far, have Network and Printer Problem"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by joshjani on 2007-04-17
As you might guess from this being posted in Absolute Beginner Talk, I am an absolute beginner to Linux and Ubuntu, though I know enough about Windows to make my wife, kids and parents think I'm a wiz! 

My parents left me their old PC when they bought a new Vista-loaded HP. This old PC they left seemed perfect as a Linux experiment, so I did a fresh install of Ubuntu Edgy. No problem with installing, and once I figured out how to get the old ISA card working, I'm on the internet with Firefox, neat as you please.

I cannot, however, seem to have any success with getting this Ubuntu machine to appear in my Windows network, nor can I print to my network printer, an HP Photosmart 2610 all-in-one. 

I have searched for help here in the forums, and almost everyone who needs printer help has a printer attached to either the Ubuntu machine or to another PC in the network. My printer has it's own spot on my network, connected via ethernet right to my Actiontec router from Verizon. So far, the tidbits I've taken away from the forums and tried have not worked. I did have a small breakthrough this AM before I came to work- I managed to get the Ubuntu machine to see one other PC in my network, a WinXP PC that sits right next to it, connected to a Netgear switch. I THINK I did this by changing the IP address of the Ubuntu PC to 192.168.1.xxx, which fits into the IP range of my home network. When I then browsed my network, though, I saw that there were two icons, one for iggynet(my network name) and one for MSHOME. In the MSHOME icon lived only the Ubuntu machine. And in the iggynet icon lived only the machine that was connected to the same switch as the Ubuntu PC. Now, I know I had one more machine on iggynet that should have shown up, but it was asleep, so I chalked that up for the moment. 

I thought that I would try to share a folder on my Ubuntu machine, so I navigated to what I thought was the system drive, found a "media" folder, and tried to make it shared. The option was grayed out. I then tried to create a new folder there, and was told I don't have permission. Huh? I am the only user of the PC, and I set myself up to have administrator priveledges. The only place I could make a new folder was right on my desktop. I created it, shared it, then looked for it on my windows network. Nothing, though the Ubuntu machine did show up under a workgroup icon in windows. I just couldn't navigate to anything on it.

I know what the IP address of the printer is, so I tried to ping it, and nothing happened. Same with the  windows PC, and with the one that was sleeping. When I try to add a printer by detecting network printers, nothing is found. If I follow the instructions and install the printer manually, it shows up as an icon in the printers folder as if it's there, but I still cannot see it, ping it, or print to it. Ubuntu tells me it's printing, but nothing actually happens.

Thanks for sticking with me so far! I suspect that if I can get the Ubuntu PC to be on the same network as the others, I'll have no trouble finding and printing to my network printer. So can any of you helpful Ubutu folks guide me, either by posting your ideas and advice or by pointing me to the proper how-tos? I feel like I'm close- I can get to the internet, I can ALMOST see the pc's from each other, etc. And as a secondary question, what am I doing wrong when I try to create a folder on the system drive? Can I get deeper permission with my login password? I guess I am confused about "root" user and administrator.

Thanks again for reading all this- I look forwrd to your tips and advice.

JC

---

### Post by freebird54 on 2007-04-17
I would start by putting the Ubuntu machine into the iggynet designation.  MSHOME and WORKGROUP are the defaults from various versions of Windows, so my guess is that it defaulted to MSHOME somwhere...

You may need to investigate Samba to access things back and forth other than the printing...

---

### Post by joshjani on 2007-04-17
> **freebird54 said:**
> I would start by putting the Ubuntu machine into the iggynet designation.  MSHOME and WORKGROUP are the defaults from various versions of Windows, so my guess is that it defaulted to MSHOME somwhere...

You may need to investigate Samba to access things back and forth other than the printing...

I thought I did put Ubuntu-PC in iggynet- I changed the domain name in Networking at least. Is there something else I need to look for and change?

---

### Post by freebird54 on 2007-04-17
Sorry - haven't dug that far into the subject yet - haven't needed anything off the other comps in the house :)

Hopefully someone with more expertise in this area will jump in soon?

---

### Post by joshjani on 2007-04-18
This is kind of a bump, and an appeal for more help, but with more information.

I have now tried to install my HP PhotoSmart 2610 network printer as each of the choices given me by ubuntu in the printers setup dialog boxes. I printed out the network settings from my printer, so I know what the IP and the hostname of the printer are. Where appropriate, I have entered that information. When I try to install the thing as a cups printer, I enter the url of [http://192.168.1.4](http://192.168.1.4), which is what the printer tells me is its IP address on my network. I then follow the rest of the setup procedure, installing an HP 2600 series printer. All is well- it seems to be there, until I try to print a test page. No joy. Nothing at all happens.

 So I delete the newly added printer, and start over, this time as a windows (smb) printer. I enter the host name of the printer, H5E-something or other, and tell it what workgroup it's in. It similarly does not allow me to print, except this time it seems to try, then I get an error saying the printer has stopped. I run upstairs to see what's up, and the printer is just snoozing away- it never knew anything was going on. If I throw something at it from an XP machine, no problem- prints right away.

I'm away from my ubuntu box right now, and I can't remember the third option, but it no worky either.

I am increasingly sure that this has more to do with getting my upuntu pc on my home network happily than with a printer specific problem. So far, I cannot get my ubuntu pc to be seen by anything on my windows network, though I can see other machines from ubuntu-pc. But, if I look at my network servers on ubuntu-pc, I see that I have two workgroups- iggynet (mine) and MSHOME, which I don't want. Ubuntu-pc is the only one in the MSHOME group, and I want it in iggynet. I have tried to just type in the workgroup I want it in, I have tried to simply delete the MSHOME icon (didn't allow me to), and I even installed the netBIOS protocol on one XP machine, since I read somewhere that the samba stuff in ubuntu had something to do with netBIOS. 

So I'm stumped, especially because I don't know what I'm doing in the first place, I'm just following onscreen directions for the most part.

If it helps, my network consists of an Actiontec wired/wireless router, to which I have directly connected the HP printer, a mac, and one XP machine. In the last port I have a netgear switch, to which I have connected ubuntu-pc and one other XP machine. XP laptops connect wirelessly to this setup as needed, and can be navigated from the ubuntu-pc.

Please, any thoughts, tips or tutorials? I want to love ubuntu, but so far I have naught but frustration!

Thanks in advance-
JC

---

### Post by freebird54 on 2007-04-18
Haven't done this - but it might help in your situation. (no guarantees!)
```

gksudo gedit /etc/cups/printers.conf
```

find your printer and change the line :

```
DeviceURI smb://WORKGROUP/HOSTNAME/sharename
```

or whatever it actually says to

```
DeviceURI smb://Guest@WORKGROUP/HOSTNAME/sharename
```

then restart your cups server and print a test page,  End Quote!

Here's another info link  [http://www.linuxprinting.org/~till/printing-tutorial/tut.html](http://www.linuxprinting.org/~till/printing-tutorial/tut.html)

Sorry I'm not an expert on this stuff yet  :)






Does this apply to your setup?

---

### Post by Robynsveil on 2007-04-18
A few quick questions: 
can the other computers see each other on your router-based network?
You haven't mentioned Samba. Is that installed? 

It seems to me that the router is acting as a sort of dhcp server. If you have assigned a static address to your Ubuntu machine, dhcp won't like it. At least, that has been my experience with the dhcp component in ICS (a workgroup based Internet-Connection sharing feature of Windows 2000 Professional).

Those drives will need to be shared using Samba for Windows users to even see them. I'm not a really good resource yet for setting up Samba... yet. Be here long enough on this forum and anyone will be, I suppose.

Sorry I haven't answered any of your questions or solved your problem, but perhaps opened a new line of thought??? :confused:

---

### Post by Robynsveil on 2007-04-18
> **joshjani said:**
> As you might guess from this being posted in Absolute Beginner Talk, I am an absolute beginner to Linux and Ubuntu, though I know enough about Windows to make my wife, kids and parents think I'm a wiz! 

Nothing like Linux to take that reputation and tromp it underfoot. I've been doing DOS and WIndows in a variety of flavour and vintages for decades, and I'm struggling too.
> **joshjani said:**
> 
I thought that I would try to share a folder on my Ubuntu machine, so I navigated to what I thought was the system drive, found a "media" folder, and tried to make it shared. The option was grayed out. I then tried to create a new folder there, and was told I don't have permission. Huh? I am the only user of the PC, and I set myself up to have administrator priveleges.

That is one of the beautiful things about Linux, as you will find... nothing is really yours to write on (owned by root) until you explicitly make it so. That is what makes Linux so safe. Annoying for ex-Windows users, but in the final analysis, heaps safer! You will need to chmod whichever folder you want to write to and change the permissions... and to do so, you need to be root (I think su works too) - something kinda like (this is in Terminal mode - have you met Terminal? - kinda like the DOS prompt, but on steroids!):
```

sudo chmod 777 /the/fully/qualified/path

```
I've found that once I've done that, I can now write to the folder. However, it's a good idea to change it back if it's not a folder you want to be adding to or changing a lot (kinda like you wouldn't want C:\Windows|system32 written to or changed without your express intentions.

As opposed to Windows where you are given all permissions, in non-root mode Linux gives you none. That is a good thing. As a principle, do as little as possible in root mode, only when you need to, and get out when you're finished doing that *administrative* task.

---

### Post by willskills on 2007-04-18
> **Robynsveil said:**
> You haven't mentioned Samba. Is that installed?  Please check this Robynsveil, and let us know!

In simple terms, SAMBA makes linux talk to windows shares and vice versa (guys please correct me if I'm wrong)

---

### Post by Seisen on 2007-04-18
Your right about samba the problem is samba is a pain in the butt to get to work sometimes. Read the post by Mitch C. and see if that helps you any.

[http://ubuntuforums.org/showthread.php?p=1561331]("http://ubuntuforums.org/showthread.php?p=1561331")

---

### Post by joshjani on 2007-04-18
> **Robynsveil said:**
> A few quick questions: 
can the other computers see each other on your router-based network?
You haven't mentioned Samba. Is that installed? 

It seems to me that the router is acting as a sort of dhcp server. If you have assigned a static address to your Ubuntu machine, dhcp won't like it. At least, that has been my experience with the dhcp component in ICS (a workgroup based Internet-Connection sharing feature of Windows 2000 Professional).

Those drives will need to be shared using Samba for Windows users to even see them. I'm not a really good resource yet for setting up Samba... yet. Be here long enough on this forum and anyone will be, I suppose.

Sorry I haven't answered any of your questions or solved your problem, but perhaps opened a new line of thought??? :confused:

Yes, all of my XP machines can see each other. My router IS a DHCP server, and I have ubuntu-pc set to work automatically that way, that is, I do NOT have it set as a static IP. And agiain, I CAN see my XP machines FROM ubuntu-pc, just not the other way around.

As far as I know, Samba is installed- or whatever comes with my Edgy install is installed. I looked at Add/Remove to see if I could add Samba components or something, and the button is green, with no further expansion available, so I guess it's there. Should I go and get a full-boat samba download?

---

### Post by joshjani on 2007-04-18
> **freebird54 said:**
> Haven't done this - but it might help in your situation. (no guarantees!)
```

gksudo gedit /etc/cups/printers.conf
```

find your printer and change the line :

```
DeviceURI smb://WORKGROUP/HOSTNAME/sharename
```

or whatever it actually says to

```
DeviceURI smb://Guest@WORKGROUP/HOSTNAME/sharename
```

then restart your cups server and print a test page,  End Quote!

Here's another info link  [http://www.linuxprinting.org/~till/printing-tutorial/tut.html](http://www.linuxprinting.org/~till/printing-tutorial/tut.html)

Sorry I'm not an expert on this stuff yet  :)






Does this apply to your setup?

Ppfff!!! You look a lot more expert than I do, that's fer sure! Thanks-

---

### Post by freebird54 on 2007-04-18
The impression is support only by hot air and Google :)  It sounds like (from the link I provided) you only need the smb client side running - and then the designation of the printer as item@place should work.  Don't know what the default status of Samba installs is.  Might be different on different version of Ubuntu too!  I'm on Edgy, with a 'test' install of Feisty in another partition - so its always fun trying to keep track...

---

### Post by willskills on 2007-04-18
Samba is a pain to get running if you are using DHCP on your network (if it's not essential) just give everyone static IPs.

As to not being able to see the Ubuntu box from your windows shares, just fire up explorer and do 

\\hostname_of_*nix_box - and you should be presented with a login window to enter your account to connect to the Ubuntu box (this should match your Samba account)

I am not sure about getting it to show in "My Network Places" - but someone else might :)

---

### Post by joshjani on 2007-04-18
> **willskills said:**
> Samba is a pain to get running if you are using DHCP on your network (if it's not essential) just give everyone static IPs.

As to not being able to see the Ubuntu box from your windows shares, just fire up explorer and do 

\\hostname_of_*nix_box - and you should be presented with a login window to enter your account to connect to the Ubuntu box (this should match your Samba account)

I am not sure about getting it to show in "My Network Places" - but someone else might :)

If the name of my ubuntu box is ubuntu-pc would I type:

\\ubuntu-pc

and that's it? Then would I put in my name and password for my ubuntu pc? What I input at login?

---

### Post by joshjani on 2007-04-18
I think this got my printer trouble solved- I was able to print a test page once I set my Photosmart 2610 up like this:

[I]Re: Problem installing HP printer - anyone help me out please ?? 

--------------------------------------------------------------------------------

Hi, I had difficulty getting my printer to work and here is how I solved the problem:
My box, hooked to D-link DSL-604+ router and HP Deskjet 6840 also pluged into the router

System--Administration--Printing:
Select "Install new printer"
Select "Network Printer"
Select "HP JetDirect"

Next step:
Host: Type in the IP Address for the printer which I got from the "print report" function on the printer.
Port: 9100 (this was already filled in)

Select Printer model
The driver is automatically selected by checking your printer model
I did not have to install any driver steps

Description: the printer
Location: on my desk

Then I was happy and it worked. There was an option to print a test page and it worked.

Hope this helps, it was the result of much trial and error with CUPS and all that stuff
Philip.[/I]
AND-

[I]In the Jetdirect printed report there is a HOST NAME ie: (NPI1AC579). This is NOT to be entered. The IP ADDRESS must be entered on that line. This has not been clear in any of the posts. Good Luck
Carl[/I]

This info is from this thread:

[http://ubuntuforums.org/showthread.php?t=365653]("http://ubuntuforums.org/showthread.php?t=365653")

Thanks to Philip and Carl! My 2610 is working, and maybe this will help someone else out!

JC

---

