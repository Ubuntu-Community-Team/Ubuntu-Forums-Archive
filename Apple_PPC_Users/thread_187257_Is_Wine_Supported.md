---
title: "Is Wine Supported??"
date: 2006-06-02
forum: Apple PPC Users
---

### Post by areitze on 2006-06-02
I've been thinking of playing around with wine to get MSN messenger running withe the help of Wine.  But seems that everywere my PPC chip is not welcome...  keep getting error for installing Wine under source to my system.

What I'm trying is to get VoIP to run normally...  basically I used Skype, but since no can do, maybe Wine can help, then I said, why stick to Skype if wine can take MSN Messenger...   But got stuck under the wine part...  

Any suggestions???
Thx,
ARV.-

---

### Post by sulobanks on 2006-06-02
Wine won't work on PPC to my knowledge.  I'm not sure what Ekiga can do, since I haven't used it, but you might check that out.

---

### Post by philipacamaniac on 2006-06-02
Wine is only a reimplementation of the Windows API. It is NOT an x86 emulator, so if you are on a different platform (read: PPC/SPARC/ARM, etc), Wine won't do you any good. All it does is load Windows x86 binaries into the X Windows environment.

If you had an Intel Mac, that would be a different story.

Some of your other options may be to try Qemu (an x86 emulator) or VMWare. Or, why don't you just use Skype for Linux???

---

### Post by BoneKracker on 2006-06-03
Have you tried Gaim (which is a standard part of the Ubuntu distribution)?  

It might not have every function in MSN messenger, but it's supposed to be able to talk to it (along with AIM and ICQ, Yahoo Messenger, IRC, Jabber, Gadu-Gadu, SILC, GroupWise Messenger, Lotus Sametime, and Zephyr.

[http://gaim.sourceforge.net/](http://gaim.sourceforge.net/)

---

### Post by 3rdalbum on 2006-06-03
[QUOTE=philipacamaniac]
Some of your other options may be to try Qemu (an x86 emulator) or VMWare. Or, why don't you just use Skype for Linux???[/QUOTE]

Typo-watch: It should've said "Skype for OS X".

---

### Post by Ububurns on 2006-06-03
philipacamaniac, Skype is not available for PPC architecture (this forum deals with PPC). Nor can it be compiled on a PPC due to the fact that Skype have not released any source code.

BoneKracker, Gaim has no voice capabilities, regardless of what chat protocols it supports.

Areitze, you have very few options.  Both Skype and Gizmo are out of the picture as they are compiled only for x86.  From what I can gather there are only two choices:

One is Ekiga.  Ekiga accounts are free (PC to PC) and users can call Google Talk and Skype friends etc.

The other choice is to compile Wengo from source ([www.openwengo.org)](www.openwengo.org)).  Wengo looks great, and does all Ekiga can do (and in my opinion, does it better).

Both programs offer PC to landline calls (requires the user to buy credits) and video calling.

I have been unable to compile Wengo successfully on PPC - but source code is available.  As far as I know Ekiga works ok... but I can't manage to get it to even call the test to see if it works.

Hope this helps.

---

### Post by areitze on 2006-06-03
[QUOTE=Ububurns]philipacamaniac, Skype is not available for PPC architecture (this forum deals with PPC). Nor can it be compiled on a PPC due to the fact that Skype have not released any source code.

BoneKracker, Gaim has no voice capabilities, regardless of what chat protocols it supports.

Areitze, you have very few options.  Both Skype and Gizmo are out of the picture as they are compiled only for x86.  From what I can gather there are only two choices:

One is Ekiga.  Ekiga accounts are free (PC to PC) and users can call Google Talk and Skype friends etc.

The other choice is to compile Wengo from source ([www.openwengo.org)](www.openwengo.org)).  Wengo looks great, and does all Ekiga can do (and in my opinion, does it better).

Both programs offer PC to landline calls (requires the user to buy credits) and video calling.

I have been unable to compile Wengo successfully on PPC - but source code is available.  As far as I know Ekiga works ok... but I can't manage to get it to even call the test to see if it works.

Hope this helps.[/QUOTE]

Hi Ububurns...   You mean the Ekliga can work to comunicate with voice to Skype Useres???  If so, it's solved, that is what I need.  Flash I can live with out, but VoIp no.  I never use MSN for voice, since in Mac it's not available, but thought that if wine could work, I could get all the MSN features working.  

But I need VoIP with Skyoe Users...  I use Gaim all day, love it, I use Adium under OS X.

So now all I'm missing is WEP-PSK for my Wifi...  jejje

I have an iBook, 1,2Ghz PPC with 768 Ram, Dual boot to OS X and Linux.  Ubuntu.  Mostly been under Ubuntu this last week, so now I'm back in OS X and feel weird...  jejej  I still feel OS X so good, but love the freedom of Open Source, download everything, get all you need, Free and help other in getting there...

Os X, buy your stuff and download just few things, but nothing really good.  iLife, buy it, iWorks, Buy it. Office, Buy it, the OS, Buy it.  The funny part is that Apple gets all the OS for the Server and most part of the desktop OS from Open Source...  

Well I'm going to explore that Conection to Skype users in Ekiga.

Thx,
ARV.-

---

### Post by areitze on 2006-06-03
Darn, new I shouldn't have celebrated to soon.  Ekiga doesn't work, and doesn't pretend to work with Skype.

Quote From the FAQ of Ekiga page.
1.1.4. What is it compatible with?

Ekiga is compatible with any software, device or router supporting SIP or H.323. It includes SwissVoice, CISCO, SNOM, ... IP Phones, but also software like Windows Messenger, Netmeeting, SJPhone, Eyebeam, X-Lite, ... or also the Asterisk popular IPBX, as well as any other commercial or Open Source IPBX. Ekiga is not compatible with Skype and will never be as long as their protocol will stay proprietary. We do not think using closed protocols for communications is a good thing. 

I support the idea of open protocol, but will not get all the people to Ekiga just to get in touch with me...

ARV.-

---

### Post by Ptero-4 on 2006-06-03
Areitze can't you just use Skype on OSX. It's far easier than trying to fiddle with Qemu or VMWare and all those other tricks. You can use OSX trough maconlinux to have it as a kind of Wine or VMWare on your Linux session.

---

### Post by dombleu on 2006-06-04
I guess there is a simpler answer to that problem. But to my knownlegde, Qemu and Bochs works really great as a MS-(whatever-it-should-be-called) emulator. Bochs is a little on the slow side thought. But both can run MS stuff, if you're not looking for performances...

Dom

---

### Post by 3rdalbum on 2006-06-04
I have a fairly new PC, and I don't think QEmu would run Windows quickly enough to be able to compress and decompress Skype audio AND run a full operating system. If you had a really fast Powermac and you used a lightweight Linux, with Skype/Linux, you *might* get it working well enough?

---

### Post by DA_uf on 2006-06-18
Maybe Darwine can help you on PPC?

[http://darwine.opendarwin.org/](http://darwine.opendarwin.org/)

---

