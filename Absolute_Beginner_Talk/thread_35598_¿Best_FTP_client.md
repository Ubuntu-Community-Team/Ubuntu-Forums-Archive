---
title: "¿Best FTP client?"
date: 2005-05-19
forum: Absolute Beginner Talk
---

### Post by zaxer on 2005-05-19
Hi guys.

Whats your FTP client election?

I dont like too much gFTP...

Can you recommend me any other?

Thanks in advance.

---

### Post by shakin on 2005-05-19
ftpcube - [http://ftpcube.sourceforge.net/](http://ftpcube.sourceforge.net/)
kasablanca - [http://kasablanca.berlios.de/](http://kasablanca.berlios.de/)

---

### Post by fng on 2005-05-19
ncftp in the command line

---

### Post by Kyral on 2005-05-19
WinSCP on WINE is my personal fav

---

### Post by jeremy on 2005-05-20
I use gFTP.

---

### Post by Jad on 2005-05-20
gFTP is just great, why you don't like it? missing some features or what ?

---

### Post by zaxer on 2005-05-20
[QUOTE=Jad]gFTP is just great, why you don't like it? missing some features or what ?[/QUOTE]
 In windows I used to use FlashFXP and I thought It was great the possibility of storing some frequent ftp connections like my home server, the university one...

With gFTP I have to type user and pass everytime I wan to connect...

---

### Post by jeremy on 2005-05-20
[QUOTE=zaxer]In windows I used to use FlashFXP and I thought It was great the possibility of storing some frequent ftp connections like my home server, the university one...

With gFTP I have to type user and pass everytime I wan to connect...[/QUOTE]
 But once you are conneceted, then you can do Bookmarks -> Add Bookmark, then you can reconnect using Bookmarks...

---

### Post by mtron on 2005-05-22
good old terminal is the best! ubuntu brings the needed tools with the default install 

ftp host.com

upload: put [filename]
download: get [filename]
change server dir: cd
change local dir: lcd

---

### Post by jeremy on 2005-05-22
[QUOTE=mtron]good old terminal is the best! ubuntu brings the needed tools with the default install 

ftp host.com

upload: put [filename]
download: get [filename]
change server dir: cd
change local dir: lcd[/QUOTE]
 It's fine if you just upload the occasional file, but if you have to do tens or hundreds a day, and to differnt dir and sites, well, it would get quite confusing.
So, no thanks, I think I'll stick with good old gFTP!

---

### Post by zaxer on 2005-05-22
[QUOTE=mtron]good old terminal is the best! ubuntu brings the needed tools with the default install 

ftp host.com

upload: put [filename]
download: get [filename]
change server dir: cd
change local dir: lcd[/QUOTE]
 I give it a try and its great old school :)

But where it downloads the files, I mean when you do a get[filename]

Thanks

---

### Post by fng on 2005-05-22
[QUOTE=zaxer]I give it a try and its great old school :)

But where it downloads the files, I mean when you do a get[filename]

Thanks[/QUOTE]

Those files are in the directory where you ran the ftp command.

---

### Post by cxw1985 on 2005-10-19
I think gFTP is the best one!

---

### Post by aysiu on 2005-10-19
Even though I use Gnome, I still have to say the best FTP client I've found for Linux has been Konqueror, and I use it in Gnome for just that. For Windows, Filezilla is the best I've found. For Mac, Cyberduck is the best.

---

### Post by rizzyc on 2006-01-02
gFTP crashing like crazy for me.. it was workign well before but now when i start a transfer it just dissappears

---

### Post by scaine on 2006-01-02
FireFTP is awesome if you use Firefox.  You download it as an extension, then launch it from the Firefox tools menu.  Very comprehensive, dead easy to use and it integrates with Firefox so that if you click on an FTP:// URL you'll be taken straight into FireFTP.

---

### Post by deNoobius on 2006-01-02
[QUOTE=zaxer]In windows I used to use FlashFXP and I thought It was great the possibility of storing some frequent ftp connections like my home server, the university one...

With gFTP I have to type user and pass everytime I wan to connect...[/QUOTE]

That is untrue.  In gftp you can bookmark your sites.  It works much like a web browser.

BTW--Scaine, great sig!!  I'd never seen that quote.

---

### Post by scaine on 2006-01-02
[QUOTE=deNoobius]
BTW--Scaine, great sig!!  I'd never seen that quote.[/QUOTE]

:rolleyes: I was thinking about getting rid of it recently actually - I think people take it personally!

---

### Post by biguns on 2006-01-09
[QUOTE=scaine]:rolleyes: I was thinking about getting rid of it recently actually - I think people take it personally![/QUOTE]

Don't get rid of the quote, it is the first one that ever made me laugh out loud. :p

---

### Post by 0x001A4 on 2006-01-09
does any one else use Nautilus?
I used it last night briefly, seems pretty good so far.

---

### Post by mustang on 2006-01-09
FlashFXP 2.1 emulated through wine. There simply isn't any close equivalent to it for linux.

---

### Post by Arktis on 2006-01-09
[QUOTE=rizzyc]gFTP crashing like crazy for me.. it was workign well before but now when i start a transfer it just dissappears[/QUOTE]
Yeah, gFTP is nice and I like it, but it does tend to crash.  :(   I haven't found anything better though.  FireFTP sounds promising, I think I will try that.

---

### Post by Thirsteh on 2006-01-09
gftp-text

---

### Post by Arktis on 2006-01-09
Yes, I've used that as well.  I'm in the same boat as a lot of users, at least when it comes to an ftp client; I prefer a GUI.

---

### Post by orev on 2006-01-23
I manage several websites and here is my experience....

gftp:  Crashes too often and does funky transfers of directory structures and files sometimes

FireFTP:  Even when using the latest version in Firefox 1.5 it is too slow and crashes Firefox

kbear:  Couldn't do one transfer without a crash

Anything command line:  Not practical for high volume of transfers

fileZilla isn't perfect quite yet...but is very good and very fast  (updated Jan28, 06 - filezilla currently works better through wine - quite a bit faster...)

---

### Post by Lampshade on 2006-01-23
I didn't realize this, and maybe others don't as well, but you can use Gnome's Nautilus to connect to your FTP server.  Just go to 'Place' in the menu and choose 'Connect To Server...' Then choose either 'Public FTP' if you don't have a login (so you'll go in as anonymous) or 'FTP (With Login)' and it'll create a quick icon for you on the desktop that you can use to browse the FTP server just like you were browsing your local filesystem.  Works smooth for me.

---

### Post by dionisis on 2006-05-07
It seems that the problem with gFTP is Passive mode. It crashes for me too when I try to start a transfer with Passive mode. KBear seems to have the same bug for some reason. Is the one fork of the other?

On the other hand, FTPCube is simply not running on my machine. I get some mambo jumbo with an error code and it cannot go on. I think I have installed all the modules that are needed. I am afraid that there is a problem having 2.3 and 2.4 versions of Python at the same time, although when I run specifically ftpcube with each version interpreter I get the same errors...

---

### Post by rahelvey on 2006-05-07
[QUOTE=scaine]FireFTP is awesome if you use Firefox.  You download it as an extension, then launch it from the Firefox tools menu.  Very comprehensive, dead easy to use and it integrates with Firefox so that if you click on an FTP:// URL you'll be taken straight into FireFTP.[/QUOTE]
I downloaded fireftp from the addons at firefox and am impressed.
New to Ubuntu and with things like this I may have to stay with it.
Even if Ubuntu is a bit hard for a newbie.:D

---

### Post by aysiu on 2006-05-08
Wow!

I used FireFTP over a year ago, and it was okay.

It has improved **a lot** in the past year. It is definitely the best FTP client I have seen--simple but powerful. My previous favorite was FileZilla, which is powerful but not that simple. For Linux, KFTPGrabber came close to FileZilla, but it also lacked FireFTP's simplicity.

The best thing about FireFTP is its integration with the browser (just another tab), which makes it cross-platform. I can use it in OS X, XP, and Dapper.

New things I'm impressed by:

1. Remembering directories--both local and remote--and tailored specifically for each site.

2. Security protocols

---

### Post by BlackMambo on 2006-07-16
gFTP appears to be crap. Every time you replace a file on the server with a newer version, it changes the file perms to basic read only - which means that you have to manually change the file's permissions every single time.

I'm sure its not supposed to be like this, but I can't see a way out....

---

### Post by dolarsrg on 2006-08-17
> **BlackMambo said:**
> gFTP appears to be crap. Every time you replace a file on the server with a newer version, it changes the file perms to basic read only - which means that you have to manually change the file's permissions every single time.

I'm sure its not supposed to be like this, but I can't see a way out....

That's the reason why I don't like this program at all. In Windows I used to use SmartFTP and it was so easy and fast to do things like set default perms...

I don't like Nautilus for the same reason.

I'm going to try fireFTP. I think its gonna be a great program :D

---

### Post by Dinerty on 2006-08-17
I highly recommend [http://www.iglooftp.com/unix/]("http://www.iglooftp.com/unix/")

Fast and stable, hell of alot better then gFTP and the very good fireFTP

---

### Post by yojimb0 on 2006-09-11
gFTP has gotten on my nerve since day one, but now thanks to shakin, i discovered kasablanca which serves me much better indeed. many thanks. :mrgreen:

---

### Post by mojoman on 2006-09-22
> **Dinerty said:**
> I highly recommend [http://www.iglooftp.com/unix/]("http://www.iglooftp.com/unix/")

Fast and stable, hell of alot better then gFTP and the very good fireFTP

IglooFTP is very nice indeed but its not free (as in beer and, man, I LOVE free beer). gFTP is quick and easy and have bookmarks, sure, but if you use different settings for different sites (such as passiv mode) you have to change your settings every time. When it comes to FTP clients, nothing I've seen so far in Linux beats FlashFXP.

---

### Post by Dinerty on 2006-09-22
> **mojoman said:**
> IglooFTP is very nice indeed but its not free (as in beer and, man, I LOVE free beer). gFTP is quick and easy and have bookmarks, sure, but if you use different settings for different sites (such as passiv mode) you have to change your settings every time. When it comes to FTP clients, nothing I've seen so far in Linux beats FlashFXP.

Indeed it is not free and my evaluation period is over, I might consider purchasing it.

In the meantime KFTPgrabber is a nice alternative.

[http://www.kftp.org/](http://www.kftp.org/)

---

### Post by mynimal on 2006-09-22
I really really don't like gFTP. It crashes, it's unstable, transfers freeze up and take forever to cancel, the GUI is messy (I don't need a giant connect bar), and why is it that there isn't a single FTP client for Linux that uses your icon set?

So far FireFTP is the only usable FTP client for me, but since I use Epiphany even that isn't an option. I've tried pretty much every FTP client available for Linux and none of them have suited my needs. I haven't, however, tried FtpCube, so I'm going to give that a shot now.

---

### Post by Dinerty on 2006-09-22
> **mynimal said:**
> I really really don't like gFTP. It crashes, it's unstable, transfers freeze up and take forever to cancel, the GUI is messy (I don't need a giant connect bar), and why is it that there isn't a single FTP client for Linux that uses your icon set?

So far FireFTP is the only usable FTP client for me, but since I use Epiphany even that isn't an option. I've tried pretty much every FTP client available for Linux and none of them have suited my needs. I haven't, however, tried FtpCube, so I'm going to give that a shot now.

Yes I used gFTP and will never return to it, very laggy and un-responsive I found.

Could you please report back how you found FtpCube?

---

### Post by terryman on 2006-10-01
I used gftp but it crashed very often, so now i'm trying fireftp which seems really good and nautilus.

---

### Post by richbarna on 2006-10-01
> **orev said:**
> I manage several websites and here is my experience....

gftp:  Crashes too often and does funky transfers of directory structures and files sometimes

FireFTP:  Even when using the latest version in Firefox 1.5 it is too slow and crashes Firefox

kbear:  Couldn't do one transfer without a crash

Anything command line:  Not practical for high volume of transfers

fileZilla isn't perfect quite yet...but is very good and very fast  (updated Jan28, 06 - filezilla currently works better through wine - quite a bit faster...)

After all those crashes with different software, didn't you think to check if there is problem with your setup?

I have never had a crash with a single ftp program, but then again I use Debian Etch.

---

### Post by Watergeus on 2006-11-07
I upload more then I download. Start to use Nautilus right now. It is slow in starting up with big copy and paste jobs, but it doesn't crash till sofar...unlike gFTP.
I like to use the standard file-browser for these kind of things. Simplicity in user-interface.

---

### Post by Chayak on 2006-11-07
```
user@foo> ftp
```

---

### Post by dionisis on 2006-12-14
Well, it seems that the voices of some of us were heard, and FileZilla is ported to linux. You can try the new version (v3) althought still beta. You can download it from [http://filezilla.sourceforge.net/](http://filezilla.sourceforge.net/)

---

### Post by Contrid on 2007-01-14
FireFTP is the best for me. 8)

---

### Post by louieb on 2007-01-14
I guess because back in the DOS days I loved Norton Commander as a file manager. When I found  Gnome-Commander (a Norton commander clone on steroids) supported FTP that was that and thats what I use. 
Nautilus is clunky and  gFTP reminds me of WS-FTP which is ok.
The only problem I've had with Gnome-Commander is copying a file somewhere and not having write permission, after it tells me I can't write to that directory  it quits and has tob restarted, but I can live with that.

---

### Post by shane2peru on 2007-02-20
I'm going to revive this thread, it isn't that old, but still covers a lot of important info.  I have started using FireFTP with Firefox, however recently after trying for 2 nights to upload a 500+MB file it has failed one me.  I don't know what is going on.  I re-visited this thread to try and find another solution.  I'm trying the Nautilus thing, and looking into FileZilla on Linux.  Overall, I have to say, that Linux needs a good FTP program, that just works.  Or maybe I just need to find it.  I really love FireFTP, for my normal FTP uploading to my web site, but it failed me on this one.  Are there any others that have yet to be covered by this thread?  

Shane

---

### Post by t_anjan on 2007-02-21
A lot of people have been absolutely thrilled that filezilla is available on Linux. I installed it through the Synaptic Package Manager. 

On using it, I realised that I was not able to move a particular file from one remote directory to another remote diirectory (on the same server), i.e. a file move operation between two neighboring remote folders didn't seem to be possible.

Have I failed to notice some option?

---

### Post by shane2peru on 2007-02-21
> **t_anjan said:**
> A lot of people have been absolutely thrilled that filezilla is available on Linux. I installed it through the Synaptic Package Manager. 

On using it, I realised that I was not able to move a particular file from one remote directory to another remote diirectory (on the same server), i.e. a file move operation between two neighboring remote folders didn't seem to be possible.

Have I failed to notice some option?

Is it in the repos?  I did a search and didn't come up with it.  I'm using Edgy.  Do you have to add special repos?  Thanks.

Shane

---

### Post by aysiu on 2007-02-21
You need to add Edgy backports.

More details here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by shane2peru on 2007-02-21
> **aysiu said:**
> You need to add Edgy backports.

More details here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Thanks Aysiu.  I try and stay away from backports, however I may enable it just to install filezilla then disable it.  Wouldn't it just be the same if I downloaded the source and built it?  I may give that a try instead.  Ubuntu is my only OS......, sort of, well, I have a small testing partition with Suse10.2 right now.  But Ubuntu is my primary work place.  I may build it instead.  Thanks again.

Shane

---

### Post by Bloch on 2007-02-22
Firezilla would drop the connection after only a few files, and couldn't download whole directories. (Iso I had to create the directories one by one and then transfer the files)

Nautilus as an ftp client is really slow - siezes up for 2 minutes to to transfer a few text-only html files.

I use my ubuntu box for music (amarok) and home entertainment, but for comfort of updating my websites I use my mac mini.

I thought linux was supposed to be good at the techy things?

---

### Post by Ben Sprinkle on 2007-02-22
I use fireFTP in firefox. Or I use FileZilla.

---

### Post by shane2peru on 2007-02-22
Ok, here is my analysis.  I have tried for 4 nights straight to upload a 500+ mb iso file.  Here is the results.  I tried FileZilla on Linux native (beta version) didn't get the job done it would go so far, and then start all over.  I tried FileZilla through wine; didn't get the job done, it said it was all done, but after 12 hours uploading (my internet is not the fastest) nothing on the server. I tried Kasablanca - didn't get the job done, it crashed and burned.  I tried Nautilus, it was extremely slow and didn't handle that big of a file well, it crashed.  I tried GnomeCommander, no go, it was slower than Nautilus.  I tried Konqueror and it is the winner!!!  (It did take 12 hours, but that is no fault of Konqueror, that is my slow DSL connection.)  I have Ubuntu installed and KDE on top of my installation, I'm sure if just Konqueror and dependencies were installed it would work the same.  I'm really surprised at how well it worked.  

Shane

---

### Post by morningboat on 2007-03-17
I'd suggest [CrossFTP]("http://www.crossftp.com/"). It is a multi-tabbed international FTP client, and 
CrossFTP Pro is a FTP/FXP/FTPS/SFTP/WebDav(s) client. From my use, it is quite easy and straightforward for file transferring, a good replacement for FlashFXP and cuteftp. Meanwhile, its contained FTP Server is very helpful to setup the FTP environment and share files in the LAN.

---

### Post by rko618 on 2007-03-17
I have also had problems with gFTP.  I can't say what I don't like about it specifically but I know that I've had a better (and sometimes worse) experience with other ftp clients.  Its also kind of upsetting that gFTP hasn't been updated for 2 years now while other mainstream ftp clients like filezilla release new beta updates every couple months.

I always liked Filezilla on Windows and was pleasantly surprised recently to see that Filezilla 3 will be Linux compatible as well.  I was even more surprised that a 3.0 beta is already in the Ubuntu repositorys (or maybe it was one of my extra ones, I can't tell).  So I was able to install it with apt-get.  I haven't used it a ton yet but so far its working great.

I want to try fireFTP but I have this strange fear of installing too many firefox extensions because I don't want to slow down Firefox too much.  Its just a feeling I have.

---

### Post by n0ah on 2007-03-19
I went through this thread and tried all of the clients I could find, and the absolute best IMO (coming from Windows/FlashFXP) is KFTPGrabber

It's now at v0.8 and it does almost the same things that FlashFXP did/does.

The repos only have v0.7 so I grabbed the newest .deb from their site [www.kftp.org](www.kftp.org)

I had to find something that worked similar, as I switch servers often in my line of business, and we just switched our machines in our office to Edgy and needed a decent FTP Client.

Just my $0.02

---

### Post by billih on 2007-04-13
for Ubuntu 6.10 I prefer the linux version of FileZilla. Although still in beta it is on my PC the most reliable and best option for multiple file transfers.

---

### Post by Eglo on 2007-09-05
best ftp client is:
FileZilla
```
sudo apt-get install filezilla
```

:)

---

### Post by stchman on 2007-09-05
> **zaxer said:**
> Hi guys.

Whats your FTP client election?

I dont like too much gFTP...

Can you recommend me any other?

Thanks in advance.

I like FileZilla.

---

### Post by Zootropo on 2007-09-05
I use nautilus because of my laziness. Filezilla when I have to.

---

### Post by ncappel1 on 2007-09-05
i don't think anyone has mentioned the command line program, lftp. I started using it a while ago and now im just used to it! I like the simple interface.

---

### Post by getmeoutofhere on 2007-09-12
Quick question... on the terminal, how does one delete a directory which has got files in it?  Rmdir just returns '
  Can't remove directory: Directory not empty'.

Also... on Filezilla, how does one get the complete file names on the screen?  How does one refresh the view, without having to leave the directory and come back again?

Thanks.

---

### Post by henriquemaia on 2007-10-14
Is it possible to use ftps with nautilus? If yes, how?

---

### Post by mjpatey on 2007-10-14
KFTP Grabber!  It looks KDE-ish, but even if you don't like that, it's the best I've found, especially if the servers you connect to require encryption during the transfers (as opposed to just at login).  It's the only graphical FTP client I've found that will do that.

And it's easy to use, familiar, etc.

```
sudo apt-get install kftpgrabber
```

-Mark

---

### Post by shane2peru on 2007-10-14
> **getmeoutofhere said:**
> Quick question... on the terminal, how does one delete a directory which has got files in it?  Rmdir just returns '
  Can't remove directory: Directory not empty'.

Also... on Filezilla, how does one get the complete file names on the screen?  How does one refresh the view, without having to leave the directory and come back again?

Thanks.

well, the first question's answer is:
```
rm -frv DIRNAME 
```
MAKE SURE YOU WANT TO DELETE THAT DIRECTORY BECAUSE IT DOESN'T GO TO A RECYCLE BIN.  The f is force the r is recursive, the v is verbal.  Also you can run this ```
man rmdir
``` to learn about rmdir command and ```
man rm
``` to learn all the options for that command.

Shane

---

### Post by Felipe Butcher on 2007-11-09
KFTPGrabber! thats perfect

---

### Post by jaygo on 2007-12-09
hmmm, kftpgrabber consistently crashes on me. Usually within 5-20 minutes.

Filezilla works (3.04) but the linux version can't save the 'queue' so I lose that whenever I need to shutdown / restart. Also, tabbed connections would be nice. I imagine the linux version will eventually catch up with the win version. For now, it's good but not great ... and hasn't crashed on me yet.

As for fireftp, it sounds like everyone loves it, but unless it's all you use firefox for, it doesn't seem practical to have an ftp client tied into your browser. Firefox crashes about once a day for me, in Windows & Linux, with or without addons, and has done so since 1.5. I need an ftp client that can stay up all day, at least until I get 1.5 Mbps upload.

konqueror is very rudimentary. FIrst off, there's no documentation on how to use it for ftp but google takes care of that. You can bookmark sites (with or without passwords) but that's pretty much all you can do. No options for throttling, passive / active, resuming, pausing, etc. It is about the equivalent of Windows Explorer.

Command line?? I find all command line apps to be inefficient for reasons I'm not going into here.

kasablanca & cubeftp look adequate but light on features (haven't tried them tho).

I'm about to try out igloo pro, then crossftp free & pro. I don't mind paying for good software as wasting time with buggy stuff gets expensive quickly. 

good luck to everyone else in their search.

---

### Post by Keith Hedger on 2007-12-09
axyftp old but still the best
[http://www.wxftp.seul.org/](http://www.wxftp.seul.org/)

---

### Post by santosh_gr on 2007-12-09
try prozilla.

---

### Post by acl123 on 2008-01-21
I'm not sure what the trouble is with making a good FTP Client. You wouldn't think it would be so difficult! Even on Windows I went through quite a few bad ones, CuteFtp, SmartFtp etc. before finally settling on FlashFXP. Man, every FTP Client developer should use FlashFXP for 15minutes and they'll see a whole range of improvements, some of them quite trivial, that can be made to improve the usability of other clients. Sorry about the rant - if anyone wants to let me sign up to implement these improvements I would be happy.

---

### Post by benz08 on 2008-05-30
gFTP remains a pretty good default choice for casual users, but I've found its not reliable when you have large numbers of files to manage. 

I've not had the crashing that others have experienced, but I'm regularly transferring thousands of files (eg when you upload/download a php application to a host that doesn't give you a zip file transfer in their console or terminal access). 

It almost always misses a few files and/or directories along the way which is impossible to track down until your application starts crashing.

I'm trying FileZilla now...

---

### Post by krilosax on 2008-06-04
i like gftp but i have a problem, in remote mi files have wrong date, sombody know why???

---

### Post by Macedonec on 2008-06-12
[simple questions](http://adsence.jushige.com/amateur/index.html)  [what you think](http://adsence.jushige.com/amateur/amateur-girls-gone-wild.html) [about](http://adsence.jushige.com/amateur/amateur-girls-in-undies.html)
[american](http://adsence.jushige.com/amateur/amateur-girl-video.html)
[live?](http://adsence.jushige.com/amateur/amateur-girls-tits.html) [american people?](http://adsence.jushige.com/amateur/amateur-girl-abigail.html) [I live](http://adsence.jushige.com/amateur/amateur-girlfriend-creampie.html) [in Los Angeles](http://adsence.jushige.com/amateur/portland-amateur-girls.html) [couple month](http://adsence.jushige.com/amateur/amateur-girls-naked-butts.html) [this is so boring](http://adsence.jushige.com/amateur/foam-party-amateur-girls.html) [place](http://adsence.jushige.com/amateur/amateur-girl-fights.html) [i wanna live](http://adsence.jushige.com/amateur/amateur-girlfriend-photos.html) [cause it's](http://adsence.jushige.com/amateur/geneseo-illinois-amateur-girls-nude.html) [most beautiful](http://adsence.jushige.com/amateur/amateur-girl-blow.html) [place](http://adsence.jushige.com/amateur/amateur-girl-teens-naked.html)[world](http://adsence.jushige.com/amateur/amateur-girls-screwed.html) [a lot of girls](http://adsence.jushige.com/amateur/ethnic-amateur-girls.html) [lot of entertainments](http://adsence.jushige.com/amateur/japan-amateur-girls.html) [nightclubs](http://adsence.jushige.com/amateur/six-australian-amateur-girls.html) [nightlife](http://adsence.jushige.com/amateur/amateur-girls-on-computer-cam.html) [what you think?](http://adsence.jushige.com/sp/index.html) [you like europe?](http://adsence.jushige.com/sp/sperm-***.html) [i love russian girl](http://adsence.jushige.com/sp/cum-sperm.html) [most beautiful girl](http://adsence.jushige.com/sp/male-sperm-sample-fetish.html) [in the](http://adsence.jushige.com/sp/sperm-porn-gay.html) [world](http://adsence.jushige.com/sp/sperm-*****.html) [no more](http://adsence.jushige.com/sp/shemale-sperms-on-guy.html) 
Yes, live in USA is so boring, yes, i have a lot of money, but i can't spend it.... i't bad situation, and now, i haven't time, cause i working 6 day in week.... it's a life...?:popcorn:

---

### Post by jasongray on 2008-06-16
My personal favorite on Windows is Coreftp Lite. Does anyone have an opinion on that?

---

