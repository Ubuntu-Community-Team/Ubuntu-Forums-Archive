---
title: "printing to priner on windows machine"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by Kulgan on 2006-11-02
Hi to all

The setup at home is as such:
I have a laptop that is on the network with several other machines, including a windows box with a printer. Guess what... I want to print to it...

It is connected with one of those "printing only" cables, rather than USB. 
I have tried with the printing manager, and afterwards it appears in lists, in Open Office for example, but I can't print to it. 

I have heard something about having to set windows to accept "raw" processes, but I have no idea what that means - let alone how to do it. 

The printer is an HP Deskjet 6122 and is listed in the list of printers in the manager.

All ideas and links welcome!

Thanks,
-K

---

### Post by mahy on 2006-11-02
Have you tried gnome-cups-manager, adding a new Samba printer in it, entering the correct location and selecting the correct driver? Next, make sure the printer is set up a as 'shared printer' in the windows machine. If the driver is available, the fact that it's LPT instead of USB doesn't matter.

---

### Post by Kulgan on 2006-11-02
that's what I have been doing... I'll give it one more shot then...

I have file sharing enabled - wouldn't that mean that the printer was shared aswell?

update:
Ok, I was wrong - I just had to share the printer....

---

### Post by rlozano on 2006-11-05
> **Kulgan said:**
> that's what I have been doing... I'll give it one more shot then...

I have file sharing enabled - wouldn't that mean that the printer was shared aswell?

update:
Ok, I was wrong - I just had to share the printer....

so what do you mean when you said you just have to share the printer? share the printer where, window or ubuntu?

thanks, i just want to understand better cuz i'm having the same trouble.

---

### Post by louieb on 2006-11-05
rlozano, You need to turn on printer shareing in windows.
controlpanel>printerandfaxes>clickonprinter>share this printer.
gota go to work now.

---

### Post by Kulgan on 2006-11-05
as louie said, on windows there is a "link" in that sidebar thing when you open printers and faxes. I think I'll get a print server anyways, since I have to turn on the windows machine anyways. I knew that from the start, and didn't think it would be a problem, but now that I have that sorted I just want it to get BETTER than it already is...

---

### Post by dsarge on 2006-11-06
I cannot get my windows printer to work either. Mahy said to enter the correct location. How do I do this? I might be a complete noob, but I can't figure this out. I have entered \\scorpion (which is my windows computer) but this did not work. Could someone give me an example of the printer address in windows?

TIA

dsarge

---

### Post by Kulgan on 2006-11-06
from what I see it does not have that much effect so long as you share the printer in windows. The location is something similar to \\WINMACHINE\pinter_name - in my case \\DESKTOP\hp_deskjet_6122_series

---

### Post by dsarge on 2006-11-06
Thanks for the quick reply. I still can't access my win printer, so I think I will try editing the smb file.

dsarge

---

### Post by psycosmyth on 2006-11-06
I had this issue as well and found that my PRINTER it's self was the problem it is a cheap Lexmark that is not Linux friendly.I can transfer Ooo files to windows and print them from windows. I use a jumpdrive rather than goofing with network sharing.:cool:

---

### Post by rlozano on 2006-11-06
> **louieb said:**
> rlozano, You need to turn on printer shareing in windows.
controlpanel>printerandfaxes>clickonprinter>share this printer.
gota go to work now.

the windows config for sharing is all there, even before i posted the problem, and im only using generic printer and generic postscipt. i have a kyocera fs-720 in my windows box to share with. it's not supported so i used generic.

now im not sure why i can't print, is it because its not supported by linux (but im already using the generic stuff for everything) or i have to modify something somewhere to make this work?

would appreciate the community feedback.... thanks...

---

### Post by Kulgan on 2006-11-07
> I use a jumpdrive rather than goofing with network sharing

yeh, that works well, but I fond it kinda cool to freak people out when I print to the other computer when I'm in my room :twisted:

---

### Post by lazyart on 2006-11-07
I just did this thru the GUI and it was simple...

First, your printer is shared in windows, correct?

From ubuntu, go to Administration>Printers.  Click on new printer.  Select network and set the type as Windows Printer (SMB).  It may ask you for the password for the Windows share if you have one set.

From there, select the Host machine (the one the printer is connected to) and it should show you a list of available printers.  Pick the printer and click Forward.  For the driver, select Raw and then Queue.  Hit Forward and give it a name to reference it from Ubuntu with.

Once it shows up in the printers window, right click, get the properties and print a test page.

---

### Post by Kulgan on 2006-11-07
that's what worked for me - I just hadn't figured out that sharing the top level drives wasn't enough to share the default printer - actually had to go in and share it. Unfortuneately it means that anybody in the neighbourhood can get into the printer if they get the wireless cracked... but hey, what the hell.

---

### Post by lazyart on 2006-11-07
Nearly did that to my neighbor to show him how insecure his network is.

---

### Post by scc4fun on 2006-11-07
> **Kulgan said:**
> that's what worked for me - I just hadn't figured out that sharing the top level drives wasn't enough to share the default printer - actually had to go in and share it. Unfortuneately it means that anybody in the neighbourhood can get into the printer if they get the wireless cracked... but hey, what the hell.
As lazyart mentioned, in Windows when you share a drive/folder/printer you can set a password that someone would have to know to be able to access it. I haven't done it, but that could mean no one will print an encyclopedia to your printer without having figured out the password.

---

### Post by Kulgan on 2006-11-07
or buggered windows filesharing - which isn't harder than guessing the password anyways :/

---

### Post by nighthawke on 2006-11-13
Install Unix printer services on your printer host, enable sharing on it, finally set the printer processor to RAW mode in the printer properties/advanced/button at the bottom.
Then goto your client system, add the printer using SMB, it'll ask you for the network user name/password, I would suggest that you use administrative access if you know the pass. If not, then use a high level account user/pass to access the printer.

If all goes well and you hit the print button, you'll get a color or greyscale sheet (depending on the printer's ability) with the Ubuntu logo at the top.

---

### Post by igeterrors on 2006-11-19
This from lazyart worked for me:

> From ubuntu, go to Administration>Printers. Click on new printer. Select network and set the type as Windows Printer (SMB). It may ask you for the password for the Windows share if you have one set.

From there, select the Host machine (the one the printer is connected to) and it should show you a list of available printers. Pick the printer and click Forward. For the driver, select Raw and then Queue. Hit Forward and give it a name to reference it from Ubuntu with.

The reason it helped is that he mentioned that "HOST" refers to the name of the MACHINE the desired printer is connected to.  And I here I was guessing  whether it meant the home network or "smb" or my printer's IP address...  I'd been here for days.   

But my test page is printing as I type this!:D  Can't wait to go into the other room and find out what it says...

---

### Post by BLTicklemonster on 2006-11-22
> **mahy said:**
> Have you tried gnome-cups-manager, adding a new Samba printer in it, entering the correct location and selecting the correct driver? Next, make sure the printer is set up a as 'shared printer' in the windows machine. If the driver is available, the fact that it's LPT instead of USB doesn't matter.

A sticky candidate if ever I saw one. You have no idea how long it has taken me to find this one post and print to the printer in the next room. Thank you for that precise concise post.

---

### Post by Kulgan on 2006-11-22
> A sticky candidate if ever I saw one. You have no idea how long it has taken me to find this one post and print to the printer in the next room. Thank you for that precise concise post.

That's why we are here, isn't it! Good times, good times...

---

### Post by BLTicklemonster on 2006-11-22
One thing, though, for people who like to butt heads with things...

I don't have the printer or computer password protected, so when I was prompted for a password, I clicked on cancel and moved right along.

No password, you say? OMG!!! Computers aren't for finance stuff, so there's nothing on our computers anyone would want, and our firewall keeps grc.com guessing, so I'm not worried at all.

---

