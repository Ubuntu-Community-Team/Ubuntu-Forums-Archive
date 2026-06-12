---
title: "Gutsy can't read DVD's? Very disapointed."
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by biomedtech on 2007-10-31
I read the FAQ that recommends waiting a month to install new releases, but I just couldn't help myself. Feisty was so kickass that I couldn't wait for Gutsy.  As far as I am concerned, Gutsy is Busted, and needs to back to the drawing board. 

I understand that some media is unsupported, but a store-bought DVD movie?  What BS. 
DVD has only been around for , what, a decade or so? It's not just one commercial DVD movie, but everyone one I've tried. I am not trying to view a Nero-burned product, just wanting to enjoy Season 10 of SG-1 on Gutsy, but instead I get this nonsense about how 'can't open .vob files'. 

Feisty did not have this problem. 

Some other quirks which I addressed in seperate posts are still problems. Items such a  clock update should not be an issue at all ( I am not a programmer, but a clock update doesn't seem like rocket science to this reporter). 

very disppointed with Gutsy, in general.  gonna have to boot into Windows to watch a store-bought DVD movie. What BS.

---

### Post by Canuckelhead on 2007-10-31
Feisty did have this "problem."
There are tonnes and tonnes of posts on this.

Since the Codecs are not free they are not distributed with any version of Ubuntu.

You'll need to install the DVD codecs if that is legal in your area...

otherwise use VLC.

---

### Post by macogw on 2007-10-31
Store-bought DVDs have encryption on them to stop "piracy."  Due to US laws (the Digital Millenium Copyright Act, specifically), it is illegal to break the encryption.  It would be illegal for Ubuntu to include the tools to break the encryption to US users, so it is not included by default at all.  You need the Medibuntu repos in order to get the DVD CSS libraries and break the encryption.  It's funny that you say it's not Nero, as if Nero-burned should mean it's hard to play.  Burning from Nero would actually guarantee that it's unencrypted and playable anywhere.

If you're in the US, tell your Congressperson and Senator that the DMCA is BS.

---

### Post by rsambuca on 2007-10-31
Please don't blame the system for this.  Feisty did not play dvd's out of the box due to legal issues of the dvd codecs.  If you need to play DVD's,[ this link]("https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-dvd") has all of the necessary info.

---

### Post by sloggerkhan on 2007-10-31
Dude, you just need to install a package most likely. Chill out. US law makes it illegal for Ubuntu to play encrypted DVDs out of the box. You might have to use the medibuntu repo because of this, or see if the feisty instructions still work. ([http://www.medibuntu.org/](http://www.medibuntu.org/) )

---

### Post by Canuckelhead on 2007-10-31
Doesn't VLC play them without breaking any laws?

---

### Post by bremen on 2007-10-31
I'm sorry you're having trouble.  Unfortunately DVD playback under linux is for the most part a violation of US laws.  This is why Gutsy can't playback commercial DVDs by default.  Also Feisty, as well as every major linux distribution, suffer the same pitfall.

To get DVD playback working in Gutsy just use the Medibuntu repositories:
[https://help.ubuntu.com/community/Medibuntu?highlight=%28medibuntu%29]("https://help.ubuntu.com/community/Medibuntu?highlight=%28medibuntu%29")

These three lines are the ones you need.
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install libdvdcss2
```

---

### Post by macogw on 2007-10-31
> **Canuckelhead said:**
> Doesn't VLC play them without breaking any laws?

I just tried to play a DVD in VLC and VLC doesn't have any video stuff available during that.  I right-clicked on the DVD and picked VLC, and it brought up VLC's little menu bar thing with play, pause, etc. and a few menus, and the "Video" menu is empty.  I'm very confused as to how VLC is supposed to work.  I always use totem-xine instead.  If my DVD drive worked well enough to get through the opening menu bit of the DVD, that'd also be nice (something hardware is broken, but I don't see anything wrong and neither does one of my friends who looked at it).

---

### Post by sloggerkhan on 2007-10-31
Don't know if VLC is 'legal' or not, but I think the decryption has to do with drive read, not playback. In any case, open VLC and then hit 'open disc' and it works. My prefered DVD playback is xine-ui, though.

---

### Post by RomeReactor on 2007-10-31
> **Canuckelhead said:**
> Doesn't VLC play them without breaking any laws?

As far as I know VLC also uses [libdvdcss]("http://www.videolan.org/developers/libdvdcss.html"), [libdvdread and libdvdnav]("http://www.videolan.org/developers/libdvdplay.html") (the packages also available from the Medibuntu repository) to play DVDs.

---

### Post by crav on 2007-10-31
> **biomedtech said:**
> I gonna have to boot into Windows to watch a store-bought DVD movie. What BS.

Just so you know, a fresh bought copy of windows won't play DVDs out of the box either. Dell or HP or whomever you bought your computer from likely installed the codecs (usually in the form of PowerDVD)

tl;dr - lol hypocrisy.

---

### Post by mikewhatever on 2007-10-31
+1 crav.
My copy of XP could not play anything but MS native formats out of the box.
I think this was the dumbest complain ever made. :shock: Neither version of Ubuntu could play any proprietary formats out of the box.[-X

---

### Post by MrFSL on 2007-10-31
> **RomeReactor said:**
> As far as I know VLC also uses [libdvdcss]("http://www.videolan.org/developers/libdvdcss.html"), [libdvdread and libdvdnav]("http://www.videolan.org/developers/libdvdplay.html") (the packages also available from the Medibuntu repository) to play DVDs.

At the very least most DVD's (practically all commercial DVD's) are going to contain CSS (Content Scambling System) It is a form of encryption and therefore you would be in violation of the DMCA regardless of what program you used to accomplish this.

---

### Post by OoooMatron on 2007-10-31
LOL, I love it when these users say things like "Gutsy needs to get back to the drawing board" just because of a simple thing like not having the dvd decryption installed :lolflag:

It's a bit insulting really when someone that obviously has no knowledge on how a system works recommends that the whole project be scrapped and started again :lolflag:

---

### Post by MrFSL on 2007-10-31
> obviously has no knowledge on how a system works recommends that the whole project be scrapped and started again 

I find it inspiring! I just notified Honda that their whole Civic line needs to be taken back to square one. The windshield washer fluid doesn't squirt out of my brand new... oh wait... I have to fill it?

---

### Post by erginemr on 2007-10-31
It is strange but when I replaced the default Totem with Totem-Xine, I could play my DVD movies flawlessly without installing libdvdcss2 first (I have installed it too afterwards, just to be safe ;)).

Maybe it was because the DVD's I have were not encrypted or something. I don't know...

(P.S. The overall performance of Totem-Xine appears to be better than the default Totem-Gstreamer.)

---

### Post by biomedtech on 2007-10-31
Fiesty was my very first Linux experience,  After initial install, Feisty prompted me to go out and retrieve an additional 250+ Megs of updates. A reboot, followed by a perfect playback of Young Frankenstein DVD. Talk to whomever keeps your repositories if this is  a violation.

---

### Post by biomedtech on 2007-10-31
I don't hear a peep out of you to fix my Gutsy clock that won't take internet updates.  I just love it when know-it-alls put down newbies.

---

### Post by macogw on 2007-10-31
> **erginemr said:**
> 
(P.S. The overall performance of Totem-Xine appears to be better than the default Totem-Gstreamer.)

I agree.  Totem-xine works better for DVDs and .wmv than totem-gstreamer.

---

### Post by dpurple77 on 2007-10-31
Nobody is putting anybody down. You made a post and you got your replies. When you address an issue with attitude like yours ( talking about BS) you should expect nothing less. You even got your answers about the dvd issue thing you have and all the reason you need about why its like that. Respect that. Do some research first. Everyone is here because they want to help. As for the clock issue you have just right click on the date on the upper right corner of your screen and then click on adjust date and time. On the window that appears the second choice you have is configuration which is set to manual. Just select keep keep synchronized with internet servers. It should tell you that you need to install ntp support where you just say install and everything is ok after you chose the server you wish to keep synchronized with.  Before you start about not having it out of the box, not everybody need synchronized clocks or cares for them anyway. In Linux what is not needed is redundant. Thats why you get to install things as you need them and not have everything installed at once and overkill you system. Hope that helps with your issue.

---

### Post by hyper_ch on 2007-10-31
Just on a side-note: This guy may not be from the US so the DMCA doesn't apply. Furthermore Canonical is not incorporated in the US so US laws do not really apply there. Why does everyone always think US laws apply everywhere in the world? The US would like to see that but that's just not true. The US tries to enforce it and has some success in some parts of the world, less success on other parts of the world and no success at all in yet another part of the world.

---

### Post by macogw on 2007-10-31
> **hyper_ch said:**
> Just on a side-note: This guy may not be from the US so the DMCA doesn't apply. Furthermore Canonical is not incorporated in the US so US laws do not really apply there. Why does everyone always think US laws apply everywhere in the world? The US would like to see that but that's just not true. The US tries to enforce it and has some success in some parts of the world, less success on other parts of the world and no success at all in yet another part of the world.

Because the US's laws are the most strict regarding this and releasing a US and a non-US version would be a pain in the butt (yes, I know Mozilla used to have US, non-US, and French, but I know a guy that worked for Netscape at the time and he said he has no idea how they managed to do that without messing up)

---

### Post by hyper_ch on 2007-10-31
That's still no reason to extend the DMCA to all the world ;)

If US laws would apply everywehre then there wouldn't be any TPB anymore... I wouldn't have the right to make copies of copyrighted materials for familiy members and close friends...

And besides, having the strictest laws doesn't mean they are the best ones ;)

---

### Post by julian67 on 2007-10-31
If it doesn't comply with US laws there will be no free CD shipping to USA, no Dell pre-installed with Ubuntu and so on.  The USA is not the only country with stupid laws that make shipping libdvdcss illegal, some European states are the same.

---

### Post by macogw on 2007-10-31
But if they violate US laws, the people with the servers used to distribute Ubuntu in the US are in trouble.  If all of Ubuntu worldwide stays within the US's laws, nobody's in trouble.  You won't get in trouble in Belgium or China or Antarctica for not having DeCSS

---

### Post by hyper_ch on 2007-10-31
But you still imply that US laws need to be recognized world-wide and that's just not the case.

---

### Post by macogw on 2007-10-31
Well if the software is going to be used worldwide, the laws of ALL countries have to be recognized.  The alternative is that there is no Ubuntu in the US.

---

### Post by julian67 on 2007-10-31
Or you make 2 editions, the US and the non-US version. This happened before with encryption tools and distros that included them because it was/is illegal to export from the US certain types of encryption so Debian, for example, offered different (user selectable) downloads to the US and to outside the US.

Imo it's basically a non issue. It's so easy to add DVD support and as for codecs Ubuntu even prompts you to get them, then downloads and installs them for you.  If people need a distro with all that hard work ;-) already done there are plenty to choose from such as Linspire, Mint and so on. And if people need a totally free distro there are several of those available too including Gobuntu.

---

### Post by philinux on 2007-10-31
Forgive my ignorance of css and piracy protection.

If you legally buy a dvd you must have the right to at least play it on a machine of your choice whether a standalone dvd player or a pc. and whatever operating system.

Is it the pc playback that is supposed to be illegal? If so why?

---

### Post by julian67 on 2007-10-31
> **philinux said:**
> Forgive my ignorance of css and piracy protection.

If you legally buy a dvd you must have the right to at least play it on a machine of your choice whether a standalone dvd player or a pc. and whatever operating system.

Is it the pc playback that is supposed to be illegal? If so why?

The means to decrypt DVD is licensed to hardware manufacturers (who make DVD players) and software suppliers (who make DVD playback software like PowerDVD).  The media companies' idea is that you should have purchased PowerDVD or similar. Linspire does actually include this (edit:I think it is LinDVD from same people as WinDVD), but as an individual it is not possible to purchase/acquire DVD playback software that is licensed by the media companies so in their eyes if you use any OS other than Windows, Mac or Linspire Linux you have no entitlement or even possibility to watch your legally owned DVDs. It can even be worse as you might have the "right" OS and player but find your DVDs are inaccessible because you purchased them in or from another part of the world and they are region locked.  I found all this out in one stressful afternoon several years ago when I bought a DVD drive for my XP PC and was surprised to find I was barred by the OS, the playback software and even the player's firmware from watching my DVDs because I'd bought them online from USA (I live in UK). Several hours later I had learned a lot, felt very aggrieved,  flashed the player firmware, found and installed a region hack for Windows, changed my software player and shortly afterwards was happily ripping DVDs and sharing them with anybody who wanted them. I don't do that anymore but I don't feel guilty. The media companies forced me to do some illegal things simply to watch my own DVDs on my own PC in my own home. I paid them back a little :)

We're very lucky using Linux that this is all taken care of simply by installing libdvdcss2. It's much much easier than doing it from scratch in Windows.

---

### Post by philinux on 2007-10-31
ok, I get it.

Interesting thing is when I ran regionset it said my player had no set region would I like to set one. Obviously I declined. In windows it's set for region 2, set when I bought the pc.

---

### Post by Qinjuehang on 2007-10-31
Just download libdvdcss.
Everyone needs it toplay dvds. You computer MIGHT* come with it if you bought a ubuntu dell, and maybe the library screwed up during upgrade

---

### Post by zorkerz on 2007-10-31
man this thread got jumped all over fast. A but of needless bashing in the opening thread caused by a misunderstanding and a bit of bashing back from some of us. Too bad but im glad it settled down. Ubuntuforums has always amazed me by the incredible welcomingness it offers everyone. 

So my friends are all up stairs watching a dvd. I installed libdvdcss2 on his computer tried to play a movie in totem and it told me to install libdvdcss2 hmmm. Whats that about? I have also installed Ubuntu restricted extras package (i know this is not dvd support). He had previously installed vlc which also would not play a dvd. As a fall back we booted in vista and are crossing our fingers it does not freeze which it does all to often. Thats why i convinced him to install ubuntu in the first place. 

Oh his computer is running feisty. Any ideas whats going on?

as an aside what other packages have people installed for restricted formats and the like

---

### Post by RomeReactor on 2007-10-31
Hi. Did you install libdvdcss from the script in libdvdread (/usr/share/doc/libdvdread3/install-css.sh) or from the Medibuntu repository? as a (possible) quick workaround, if the system is using totem-gstreamer, try changing it to totem-xine:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs
```

---

### Post by mikewhatever on 2007-11-01
There is a nice interview with Clement Lefebvre, the founder of Linux-Mint. Here's what he has to say on the issue and I kind of tend to agree.

[http://www.freesoftwaremagazine.com/blogs/interview_with_clement_lefebvre](http://www.freesoftwaremagazine.com/blogs/interview_with_clement_lefebvre)

> TM: Talking about codecs... I think it's a fantastic idea. Do you feel you could end up having legal problems? What's the legal landscape like around codecs?

CL: The presence of the codecs is definitely not an innovation, it's a necessity. People do watch DVDs and they do listen to MP3s. There is no out-of-the-box experience without codecs. They need to be installed by default. There are some legal obstacles in distributing them but that only affects a few countries and for the people who actually live in these countries we have a "Light Edition" without the codecs. The legal landscape is different in every country and to be honest it's more of a user matter than anything else. When users are in doubt we recommend they install the "Light Edition" but as far as we're concerned it's 100% legal for us to do what we do where we do it. There's a lot of FUD and bullying related to software patents, something that simply has no legal standing where we are and it's time people realize that there is no legislation in the world which is going to prevent us doing anything where that legislation doesn't apply.

---

### Post by zorkerz on 2007-11-01
Where are they? My impression is that the US tends the be the most strict it this regard. I also believe the US has a significant number of linux users (I could shove my foot in my mouth here. Id live to see numbers). What legal risk do people from different legal landscapes run?

---

### Post by erginemr on 2007-11-01
> **zorkerz said:**
> man this thread got jumped all over fast. A but of needless bashing in the opening thread caused by a misunderstanding and a bit of bashing back from some of us. Too bad but im glad it settled down. Ubuntuforums has always amazed me by the incredible welcomingness it offers everyone. 

So my friends are all up stairs watching a dvd. I installed libdvdcss2 on his computer tried to play a movie in totem and it told me to install libdvdcss2 hmmm. Whats that about? I have also installed Ubuntu restricted extras package (i know this is not dvd support). He had previously installed vlc which also would not play a dvd. As a fall back we booted in vista and are crossing our fingers it does not freeze which it does all to often. Thats why i convinced him to install ubuntu in the first place. 

Oh his computer is running feisty. Any ideas whats going on?

as an aside what other packages have people installed for restricted formats and the like

I also strongly encourage you to install totem-xine and thus replace the default totem-gstreamer. It is still the same program but with a Xine back end to play the videos. Although Mplayer and VLC are praised and much more popular in the Linux community, they did not work for me well especially with the subtitles.

This way, you will not need to bother whether libdvdcss2 has been installed or not (probably, I am not sure), because Xine uses its own libraries to play encrypted DVD's. 

Now that you have the Xine library already after the installation of totem-xine, you may also consider installing GXine, the gnome front-end to the once-popular, legendary Xine movie player as a backup video player. I sometimes use it instead of Totem to watch movies, because it has a simpler, to the point interface and I feel like it performs slightly better than Totem in that sense.

---

### Post by julian67 on 2007-11-01
> **erginemr said:**
> I also strongly encourage you to install totem-xine and thus replace the default totem-gstreamer. 

+1

Totem with xine backend is excellent. You'd need totem-xine, libxine1-ffmpeg, libdvdcss2, libdvdnav4, libdvdread3 and maybe w32codecs.

---

### Post by Neobuntu on 2007-11-05
This is total frekin BS! I don't care if you think I shouldn't be upset. I am!

I have a fresh install of gusty and I can't play a frekin' DVD (regular store bought)!

I have gone through numerous disorganized instructions and still no play.

I installed everything related to gstreamer codecs and it doesn't play.

I installed gxine and associated packages, switch to gxine upon inserting a DVD and it does not read the DVD path right or something. It Fails the Gxine wizard and I'm not entirely sure what it wants and why it can not find it.

I'm a frekin'  25 year computer jockey! I'm sure I can EVENTUALLY figure this out (please help) but the newbie is totally messed over and will RUN, not walk back to Windows!

Why can't we have a clear guide FOR gusty? Why doesn't the one I tried work? I know all about the legal BS. I don't care. I want ALL formats and codecs to work and if I can't have it work automatically (I understand) then clear directions sure would keep monopolist from screwing us over!

P.S. Obviously we need to stand up and correct corruptly purchased laws because IT MATTERS!

---

### Post by rsambuca on 2007-11-05
> **Neobuntu said:**
> This is total frekin BS! I don't care if you think I shouldn't be upset. I am!

I have a fresh install of gusty and I can't play a frekin' DVD (regular store bought)!

I have gone through numerous disorganized instructions and still no play.

I installed everything related to gstreamer codecs and it doesn't play.

I installed gxine and associated packages, switch to gxine upon inserting a DVD and it does not read the DVD path right or something. It Fails the Gxine wizard and I'm not entirely sure what it wants and why it can not find it.

I'm a frekin'  25 year computer jockey! I'm sure I can EVENTUALLY figure this out (please help) but the newbie is totally messed over and will RUN, not walk back to Windows!

Why can't we have a clear guide FOR gusty? Why doesn't the one I tried work? I know all about the legal BS. I don't care. I want ALL formats and codecs to work and if I can't have it work automatically (I understand) then clear directions sure would keep monopolist from screwing us over!

P.S. Obviously we need to stand up and correct corruptly purchased laws because IT MATTERS!You might want to consider something like Linux Mint, since DVD playback should work out-of-the-box.

---

### Post by stchman on 2007-11-05
> **biomedtech said:**
> I read the FAQ that recommends waiting a month to install new releases, but I just couldn't help myself. Feisty was so kickass that I couldn't wait for Gutsy.  As far as I am concerned, Gutsy is Busted, and needs to back to the drawing board. 

I understand that some media is unsupported, but a store-bought DVD movie?  What BS. 
DVD has only been around for , what, a decade or so? It's not just one commercial DVD movie, but everyone one I've tried. I am not trying to view a Nero-burned product, just wanting to enjoy Season 10 of SG-1 on Gutsy, but instead I get this nonsense about how 'can't open .vob files'. 

Feisty did not have this problem. 

Some other quirks which I addressed in seperate posts are still problems. Items such a  clock update should not be an issue at all ( I am not a programmer, but a clock update doesn't seem like rocket science to this reporter). 

very disppointed with Gutsy, in general.  gonna have to boot into Windows to watch a store-bought DVD movie. What BS.

Go back to Feisty.

Encrypted DVDs are proprietary and you need to install the CSS decryption.

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

This should do the trick.

---

### Post by Neobuntu on 2007-11-05
Thank you. Mint was on top of my list until Gusty came out. I have been generally impressed with Gusty accept for this. I feel that I can get more out of Gusty overall. Just why does adding DVD reading have to be so unclear? not being able to include it is a travesty but I get it. I just don't get why   it's harder than the Automatix days. I thought the general idea was to trump Automatix.

Could we please have an explanation of all the DIFFERING ways to play a DVD. Why is one software player better than the other. Why is totem picked if the best thing to do is replace it? I'm fine with Totem, if it works! I'm fine with something else if that's what I need to get it to work. Yet what is it?

I know all the many formats may require a different player but I'm talking about a regular DVD here. What's the game?

Are differing road blocks on differing store bought DVDs? If so, how can I test a DVD to know which problem I must overcome?

I had one backed up DVD from the same series copy to DVD-R just fine. Yet, another in the same series copied (using the same method) with encryption or something that was extremely blocky and unwatchable. How can one tell the difference?

---

### Post by LowSky on 2007-11-05
> **Neobuntu said:**
> This is total frekin BS! I don't care if you think I shouldn't be upset. I am!

um calm down its only a computer.

> **Neobuntu said:**
> I have a fresh install of gusty and I can't play a frekin' DVD (regular store bought)! 
windows cant either

> **Neobuntu said:**
> I have gone through numerous disorganized instructions and still no play.

what have you tried
> **Neobuntu said:**
> I installed everything related to gstreamer codecs and it doesn't play.
how did you install them

> **Neobuntu said:**
> I installed gxine and associated packages, switch to gxine upon inserting a DVD and it does not read the DVD path right or something. It Fails the Gxine wizard and I'm not entirely sure what it wants and why it can not find it.
Gxine shows you a error report, what does it say? Also have you tried VLC?

> **Neobuntu said:**
> I'm a frekin'  25 year computer jockey! I'm sure I can EVENTUALLY figure this out (please help) but the newbie is totally messed over and will RUN, not walk back to Windows!
again windows can't pay DVDs from a new install

> **Neobuntu said:**
> Why can't we have a clear guide FOR gusty? Why doesn't the one I tried work? I know all about the legal BS. I don't care. I want ALL formats and codecs to work and if I can't have it work automatically (I understand) then clear directions sure would keep monopolist from screwing us over!
gutsy came out 2 weeks ago... chill, give people time

> **Neobuntu said:**
> P.S. Obviously we need to stand up and correct corruptly purchased laws because IT MATTERS! 

The encryption of DVD occured because people were pirating them. a company has the right to protect its products and investments from being stolen.

If you want to fight something worth fighting, help fight Microsoft from suing linux over patent infringement that microsoft says exist but doesn't show any proof.

---

### Post by Neobuntu on 2007-11-05
OK thanks Stch.

My "css" was already the newest one. As the directions said, I'm installing VLC which from past experience I know has it's own deal and works with more stuff.

Still, why even start with Totem then? I like the controls but if I have to move away from gstreamer and perhaps Totem altogether then why am I have to do this?

I can handle it. I weep for the poor newbie.

---

### Post by Neobuntu on 2007-11-05
OK it's playing. I sure wish we had a comprehensive run down of ALL these option AND segmented for Gusty. there's a lot of old instruction and this is totally messing over the newbie. It sure hasn't saved me any time either!!!!!!!!!!!!

Thank you for you patience during my indignation.

---

### Post by rsambuca on 2007-11-05
> **Neobuntu said:**
> OK it's playing. I sure wish we had a comprehensive run down of ALL these option AND segmented for Gusty. there's a lot of old instruction and this is totally messing over the newbie. It sure hasn't saved me any time either!!!!!!!!!!!!

Thank you for you patience during my indignation.

There already are instructions, and all you had to do was look in the[ Ubuntu community documentation]("https://help.ubuntu.com/community/RestrictedFormats#head-6c1adf157cf1aaf47a391922036b3ecc98f01796").

---

### Post by mikewhatever on 2007-11-05
> **Neobuntu said:**
> This is total frekin BS! I don't care if you think I shouldn't be upset. I am!

I have a fresh install of gusty and I can't play a frekin' DVD (regular store bought)!

I have gone through numerous disorganized instructions and still no play.

I installed everything related to gstreamer codecs and it doesn't play.

I installed gxine and associated packages, switch to gxine upon inserting a DVD and it does not read the DVD path right or something. It Fails the Gxine wizard and I'm not entirely sure what it wants and why it can not find it.

I'm a frekin'  25 year computer jockey! I'm sure I can EVENTUALLY figure this out (please help) but the newbie is totally messed over and will RUN, not walk back to Windows!

Why can't we have a clear guide FOR gusty? Why doesn't the one I tried work? I know all about the legal BS. I don't care. I want ALL formats and codecs to work and if I can't have it work automatically (I understand) then clear directions sure would keep monopolist from screwing us over!

P.S. Obviously we need to stand up and correct corruptly purchased laws because IT MATTERS!

This is really silly. Why don't you figure it all out and write a good and clear guide on how to play DVDs. I suspect you do not care about it too with that egocentric fretting kind of attitude.

---

### Post by Neobuntu on 2007-11-05
Nope, sorry. That's the first thing I tried.

---

### Post by Neobuntu on 2007-11-05
Dear Mike, 

As much as I don't like anyone saying anything bad about my Ubuntu either, asking people to be completely devoid of emotions in these frustrating matters is not realistic. 

I exercised A LOT of self control in being as civil as I have and simply dismissing me as a bad attitude is nor productive nor does it help the newbie overcome these insane obstacles.

I am well capable of getting as deep as one could go AND I DON'T WANT TO WASTE TIME! I'm looking for the time saving method and if you are not, you need to catch a clue.

I do not judge myself upon how much technical difficulty I can get though and this is NOT what I think Ubuntu is or should be about.

So back to my original concern. Why does the newbie NOT find WORKING, clear, and distinguished directions? How has this been overlooked in Gusty in light of how Automatix (granted with it's own problems) works so simply. it SAVED TIME! i'm fine with going beyond Automatix. Lets do that.

Doesn't anyone care about time? 

I'm well aware that Windows sucks and doesn't start with DVD playing either. The very reason I point out a flaw in Ubuntu (which I still overall prefer; to anything) is so that in fact, the Windows convert will not be scared off by the TIME it takes to sort through these issues.

In summary, if we are playing the game of "Can't legally include it" then we need to simplify and speed up the process of ADDING it!

There needs to be a better way of communicating which instruction to follow. It needs to work (hello). We need to find a way to LEGALY include this stuff because it is monopoly anti-competitiveness.

Then there the whole issue of which player to use.

I will gladly put up with this crap compared to Windows but I fear many newbies will not. 

If your angry that I'm angry about it then lets fix it. OK? That's the point. I have every confidence that these issues can be clarified. I'm attempting to define the problem.

---

### Post by rsambuca on 2007-11-05
> **Neobuntu said:**
> Dear Mike, 

As much as I don't like anyone saying anything bad about my Ubuntu either, asking people to be completely devoid of emotions in these frustrating matters is not realistic. 

I exercised A LOT of self control in being as civil as I have and simply dismissing me as a bad attitude is nor productive nor does it help the newbie overcome these insane obstacles.

I am well capable of getting as deep as one could go AND I DON'T WANT TO WASTE TIME! I'm looking for the time saving method and if you are not, you need to catch a clue.

I do not judge myself upon how much technical difficulty I can get though and this is NOT what I think Ubuntu is or should be about.

So back to my original concern. Why does the newbie NOT find WORKING, clear, and distinguished directions? How has this been overlooked in Gusty in light of how Automatix (granted with it's own problems) works so simply. it SAVED TIME! i'm fine with going beyond Automatix. Lets do that.

Doesn't anyone care about time? 

I'm well aware that Windows sucks and doesn't start with DVD playing either. The very reason I point out a flaw in Ubuntu (which I still overall prefer; to anything) is so that in fact, the Windows convert will not be scared off by the TIME it takes to sort through these issues.

In summary, if we are playing the game of "Can't legally include it" then we need to simplify and speed up the process of ADDING it!

There needs to be a better way of communicating which instruction to follow. It needs to work (hello). We need to find a way to LEGALY include this stuff because it is monopoly anti-competitiveness.

Then there the whole issue of which player to use.

I will gladly put up with this crap compared to Windows but I fear many newbies will not. 

If your angry that I'm angry about it then lets fix it. OK? That's the point. I have every confidence that these issues can be clarified. I'm attempting to define the problem.

Sorry Neo, but I side with mike on this one.  Your first post was nothing more than an emotion filled bashing rant.  Despite what you think, the vast majority of forum users manage to convey their thoughts and articulate their questions without emotional tirades.  I suggest that in the future, if you are feeling frustrated you leave your computer for a few minutes to relax and calm down prior to posting.

---

### Post by Neobuntu on 2007-11-05
I take what you are saying but it simply wasn't that bad. you are suggesting that I act like Mr. Spoke or something and that's not wise.

I now also have the DVD playing with totem-xine. Granted it follows these directions:

> In gutsy to get encrypted DVD playback to work i had to do the following:

sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine
sudo /usr/share/doc/libdvdread3/install-css.sh

After that, running gxine from the Applications -> Sound and Video menu played the DVD perfectly. I found this tip at: [WWW] [http://yoten.blogspot.com/2007/10/play-encrypted-dvds-under-ubuntu-gutsy.html](http://yoten.blogspot.com/2007/10/play-encrypted-dvds-under-ubuntu-gutsy.html) cheers random website! 

So that this may help someone else.

Again, granted this is in the more "official" directions. The problem was the other direction that I found first. Directions that people said was the way to go. These directions were a sub link of what was suggested above and so technically yes I missed them but it wasn't without effort.

> dpkg - warning: downgrading libdvdcss2 from 1.2.9-2medibuntu4 to 1.2.5-1.

Was one out come of these directions. Why?

In the end I had to try about four differing major methods. This is the problem I am addressing.

I love choice. That's not the problem. The problem is a clear path and the reasons why.

Anger BTW is not good or bad. It's what you do about it. Anger is an excellent motivation and I am motivated! I think the community can benefit from this understanding as it relates to the new Gusty. 

I do NOT want newbies being put off. Is that hard to understand?

Thank you, to all who are working on the problem. I see great improvement. Better methods and NO other OS is better than Ubuntu.

---

### Post by John.Michael.Kane on 2007-11-05
> **rsambuca said:**
> There already are instructions, and all you had to do was look in the[ Ubuntu community documentation]("https://help.ubuntu.com/community/RestrictedFormats#head-6c1adf157cf1aaf47a391922036b3ecc98f01796").

There is a codec/flash install guide for 64bit users as well, and it should work for 32bit users with some editing. [http://ubuntuforums.org/showthread.php?t=368607]("http://ubuntuforums.org/showthread.php?t=368607")


Also I would add trying to fix any problem while being frustrated will only lead to more issues. If the problem has you frustrated step away from it go get some tea, and take a breather, and stretch. Then come back to it later, and try to solve it.

---

### Post by jaybombalous on 2007-11-05
> **dpurple77 said:**
> Nobody is putting anybody down. You made a post and you got your replies. When you address an issue with attitude like yours ( talking about BS) you should expect nothing less. You even got your answers about the dvd issue thing you have and all the reason you need about why its like that. Respect that. Do some research first. Everyone is here because they want to help. As for the clock issue you have just right click on the date on the upper right corner of your screen and then click on adjust date and time. On the window that appears the second choice you have is configuration which is set to manual. Just select keep keep synchronized with internet servers. It should tell you that you need to install ntp support where you just say install and everything is ok after you chose the server you wish to keep synchronized with.  Before you start about not having it out of the box, not everybody need synchronized clocks or cares for them anyway. In Linux what is not needed is redundant. Thats why you get to install things as you need them and not have everything installed at once and overkill you system. Hope that helps with your issue.

I agree, install ntp support, select a local time server and be done with it.

---

### Post by zorkerz on 2007-11-05
So there appear to be a few different ways to get encrypted dvd playback.

totem-xine

totem-gstreamer

vlc

I think it would be helpful if we made a list of the packages needed for each method (plus any other methods out there) and provided the repos that are needed to get the packages. 

It seems that many/most of the instructions out there have people install extra packages that are not needed specifically for encrypted dvd playback.

Maybe a list of packages and what they multimedia they allow to be played would be helpful too. Where would the best place to create this? Possibly a page on the wiki/in the community docs?

Another potential confusion is installing packages from Add/Remove Applications vs synaptic or apt-get. The problem here is Add/Remove shows a package such as 'ubuntu-restricted-extras' that in reality just depends on a number of individual packages.

---

### Post by rsambuca on 2007-11-05
> **zorkerz said:**
> So there appear to be a few different ways to get encrypted dvd playback.

totem-xine

totem-gstreamer

vlc

I think it would be helpful if we made a list of the packages needed for each method (plus any other methods out there) and provided the repos that are needed to get the packages. 

It seems that many/most of the instructions out there have people install extra packages that are not needed specifically for encrypted dvd playback.

Maybe a list of packages and what they multimedia they allow to be played would be helpful too. Where would the best place to create this? Possibly a page on the wiki/in the community docs?

Another potential confusion is installing packages from Add/Remove Applications vs synaptic or apt-get. The problem here is Add/Remove shows a package such as 'ubuntu-restricted-extras' that in reality just depends on a number of individual packages.

I think a lot of people just need to learn how to read for themselves.  We already have these things.

[Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats#head-6c1adf157cf1aaf47a391922036b3ecc98f01796") and [Restricted Formats/Playing DVD's]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by Neobuntu on 2007-11-05
I know one thing for darn sure. Telling people they are wrong for being frustrated, to take a chill pill (tea or whatever) and RTFM is not bring anyone into the Ubuntu fold. I wasn't over the top and if you think I was imperfect, you are correct. That's what human beings are.

Look, I worked out my problems and I did it fast. Everything works. It's not me I'm worried about. It is the new user.

We definitely do not need to gloss over the problem just because it pisses people off. We need to fix the problem because it pisses people off.

Don't pretend that we don't need to make it easier. Obviously, I can work it out. But so what? I'm not a complete newbie. It doesn't make me a smarter person. It needs to be technically easier, logistically easier,  searchably easier and player choices need to be more easily laid out before the new user.

The confusion has got to be stopped from the beginning.

Yes, as much as some geeks hate it, we need the one button solution.  Easier, easier and then easier. This from an overall Ubuntu point of view. THAT is the current reality.

We are certainly not competing with Windows in overall benefits. We are now competing with ourselves. Ubuntu must improve upon Ubuntu.

I come with the perspective that the newbie must be so overwhelmed with the goodness and time savings of Ubuntu that Windows (or OS-X) become irrelevant TO THEM. Not to you but to them.

If you do not think we need more people to adopt Ubuntu, we're done here. I do. If you do not believe newbies and time saving for us ALL matters, then we're done. I do.

Let me be clear. I am passionate about open software and Ubuntu. I am angered at the lack of freedoms, corrupt anti-competition and propaganda in the majority of the population. I also do not care for the brand of geek that thinks emotion is bad, and are so removed from newbies that they can't possibly make a system for everyone. That being as most people are NOT in fact technical. I'm proud to be associated with those technical people who get it. The majority of the Ubuntu community that are actively making information management easy, secure and unfettered. To those people I want to thank you for your tireless effort.

I mean come on. Can't we agree that playing a DVD should not take this much time? So in summary, just because we can't included it today, let's not leave it time consuming to add ourselves. We are proving no good point there. Onward and upward.

---

### Post by rsambuca on 2007-11-05
> **Neobuntu said:**
> I know one thing for darn sure. Telling people they are wrong for being frustrated, to take a chill pill (tea or whatever) and RTFM is not bring anyone into the Ubuntu fold. I wasn't over the top and if you think I was imperfect, you are correct. That's what human beings are.

Look, I worked out my problems and I did it fast. Everything works. It's not me I'm worried about. It is the new user.

We definitely do not need to gloss over the problem just because it pisses people off. We need to fix the problem because it pisses people off.

Don't pretend that we don't need to make it easier. Obviously, I can work it out. But so what? I'm not a complete newbie. It doesn't make me a smarter person. It needs to be technically easier, logistically easier,  searchably easier and player choices need to be more easily laid out before the new user.

The confusion has got to be stopped from the beginning.

Yes, as much as some geeks hate it, we need the one button solution.  Easier, easier and then easier. This from an overall Ubuntu point of view. THAT is the current reality.

We are certainly not competing with Windows in overall benefits. We are now competing with ourselves. Ubuntu must improve upon Ubuntu.

I come with the perspective that the newbie must be so overwhelmed with the goodness and time savings of Ubuntu that Windows (or OS-X) become irrelevant TO THEM. Not to you but to them.

If you do not think we need more people to adopt Ubuntu, we're done here. I do. If you do not believe newbies and time saving for us ALL matters, then we're done. I do.

Let me be clear. I am passionate about open software and Ubuntu. I am angered at the lack of freedoms, corrupt anti-competition and propaganda in the majority of the population. I also do not care for the brand of geek that thinks emotion is bad, and are so removed from newbies that they can't possibly make a system for everyone. That being as most people are NOT in fact technical. I'm proud to be associated with those technical people who get it. The majority of the Ubuntu community that are actively making information management easy, secure and unfettered. To those people I want to thank you for your tireless effort.

I mean come on. Can't we agree that playing a DVD should not take this much time? So in summary, just because we can't included it today, let's not leave it time consuming to add ourselves. We are proving no good point there. Onward and upward.
I agree with your points, but as my previous post shows, the info is already in the documentation.  At some point, people have to be able to read for themselves.  Also, passion is fine, but that does not mean that we should be uncivilized in our use of language.  Users of all ages frequent these forums.

---

### Post by Neobuntu on 2007-11-05
Give me a break. I said I was upset.

I don't like the extra time it took and I fear for the new users.

I work with new users to dispel the myths and lies and actually SHOW them what they can do. Their tolerance is FAR less than mine. They would just as soon stay with Windows. It's like a bad relationship. They are married to it and without a shock, they will go down with it. I suggest you think about that. The idea that it doesn't matter, is a very dangerous myth.

Like I said, perhaps first, we should all get angry and do something (good) about why we can't include things like DVD reading.

P.S. I far prefer Flash drives to messing with DVD/CDs but that's another subject.

---

### Post by rsambuca on 2007-11-05
> **Neobuntu said:**
> Give me a break. I said I was upset.

I don't like the extra time it took and I fear for the new users.

I work with new users to dispel the myths and lies and actually SHOW them what they can do. Their tolerance is FAR less than mine. They would just as soon stay with Windows. It's like a bad relationship. They are married to it and without a shock, they will go down with it. I suggest you think about that. The idea that it doesn't matter, is a very dangerous myth.

Like I said, perhaps first, we should all get angry and do something (good) about why we can't include things like DVD reading.

P.S. I far prefer Flash drives to messing with DVD/CDs but that's another subject.

I guess I am a believer that acting out of anger is never the best course of action.

---

### Post by Neobuntu on 2007-11-05
I'm glad I was able to point out that acting on anger by doing good is a positive. I never said I was perfect at it either. "Acting out" suggests a negative. Perhaps the situation and not the user,  is the more negative here.

I think you'll find many people not so carefully as I, as they may chuck Ubuntu altogether. It's not something we Ubuntu fans like to talk about but some people do try it and sadly go back to support the monopoly because their DVD does work there already. This WILL bite them in the end.  I didn't say it was fair. I'm saying it upsets me.

I don't recall the Ubuntu terms of service suggesting only emotionless posts being a requirement. I do agree that there is a balance. I think if you will read my posts in the best possible light rather than choosing the later, you'll find them reasonable.

...but you know what. I'm not up for vote here. If we try to write for every possible reader then nothing would get done. No! ... One has to say their part and let the chips fall where they may. I suppose the worst thing I typed was "BS". If you think about it, any younger readers would not know what that MIGHT stand for. If they do know, then they already know. But if it makes you feel better, I will endeavor to NOT type it any more. I do apologize even, as one of those letters is (nearly) meaningless. I do prefer real meaningful words over and above meaningless ones. I think you know my point was that something is really wrong with wasting time doing something that should already (and was already) working.

I'm getting really tired of setting up the same things over and over again! Per computer; per clean install!

---

### Post by zorkerz on 2007-11-05
thanks for your fast response rsambuca. I have frequented both of those sites and neither of them provide quite what i am looking for although i would imagine they should have enough information for most. I will try and explain better next time. 

For encrypted DVD playback support in Ubuntu:
This seems to be what everyone needs and has been linked many times here and on other threads. The links are all from the community Docs

Start with [RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats") which has you install ubuntu-restricted-extras. Then [PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs") which gives the various player options. And finally [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") to install libdvdcss2.

Most of the packages installed with ubuntu-restricted-extras are not required for encrypted dvd playback. I would like to understand which ones are?

ubuntu-restricted-extras:
&#8728; gstreamer0.10-plugins-ugly -> libmpeg2-4, libsidplay1, liba52-0.7.4
&#8728; gstreamer0.10-plugins-ugly-multiverse
&#8728; msttcorefonts -> cabextract
&#8728; sun-java6-jre -> sun-java-bin [binfmt-support, libstdc++5 {gcc-3.3-base}, unixodbc {odbcinst1debian1}], ia32-libs
&#8728; unrar
&#8728; gstreamer0.10-plugins-bad -> libcdaudio1, libjack0 [libfreebob0], libmms0, libsoundtouch1c2, libmpcdec3*
&#8728; gstreamer0.10-plugins-bad-multiverse -> libfaac0 [libmp4v2-o], libfaad2-0, libmjpegtools0c2a [libquicktime1]{libavcodec1d, libavutil1d}, libx265-54, libxvidcore4,
&#8728; gstreamer0.10-ffmpeg
&#8728; liblame0
&#8728; libdvdread3 -> {libdvdcss2} suggestion
 
sorry its a convoluted structure the bulleted items are dependent on ubuntu-restricted-extras. Packages following an arrow (->) are depended on the bulleted item. And so on with [] and {}.

I guess this is uninteresting to most people but I wanted to keep track of what was being installed and hopefully find out which few i actually need.

cheers all

---

### Post by igknighted on 2007-11-05
> **Neobuntu said:**
> I'm glad I was able to point out that acting on anger by doing good is a positive. I never said I was perfect at it either. "Acting out" suggests a negative. Perhaps the situation and not the user,  is the more negative here.

I think you'll find many people not so carefully as I, as they may chuck Ubuntu altogether. It's not something we Ubuntu fans like to talk about but some people do try it and sadly go back to support the monopoly because there DVD does work their already. This WILL bite them in the end.  I didn't say it was fair. I'm saying it upsets me.

I don't recall the Ubuntu terms of service suggesting only emotionless posts being a requirement. I do agree that there is a balance. I think if you will read my posts in the best possible light rather than choosing the later, you'll find them reasonable.

...but you know what. I'm not up for vote here. If we try to write for every possible reader then nothing would get done. No! ... One has to say their part and let the chips fall where they may. I suppose the worst thing I typed was "BS". If you think about it, any younger readers would not know what that MIGHT stand for. If they do know, then they already know. But if it makes you feel better, I will endeavor to NOT type it any more. I do apologize even, as one of those letters is (nearly) meaningless. I do prefer real meaningful words over and above meaningless ones. I think you know my point was that something is really wrong with wasting time doing something that should already (and was already) working.

I'm getting really tired of setting up the same things over and over again! Per computer; per clean install!

Use mint then, it seems to have all that stuff installed already, plus it uses the same repositories as Ubuntu, so you aren't really switching distro's, just using a different installer.

Perhaps a dvd-playback metapackage could be created, but honestly that's the only way it could get easier.  And even then you run into issues of whether to use vlc, totem (gstreamer or xine), mplayer or any other player (personally, I like KDE's Kaffeine best).  So its not as straight forward as you might imagine.

---

### Post by rsambuca on 2007-11-05
> **Neobuntu said:**
> 
I'm getting really tired of setting up the same things over and over again! Per computer; per clean install!

Then install Mint or PClinuxOS.  They have the codecs installed by default.  Ubuntu doesn't, and if you care to read the philosphy behind it, you would understand why.  You are complaining about Ubuntu for doing exactly what it sets out to do.

---

### Post by Neobuntu on 2007-11-05
> **igknighted said:**
> Use mint then, it seems to have all that stuff installed already, plus it uses the same repositories as Ubuntu, so you aren't really switching distro's, just using a different installer.

Perhaps a dvd-playback metapackage could be created, but honestly that's the only way it could get easier.  And even then you run into issues of whether to use vlc, totem (gstreamer or xine), mplayer or any other player (personally, I like KDE's Kaffeine best).  So its not as straight forward as you might imagine.

What part of, I prefer Ubuntu and I now have it working in Ubuntu did you not understand? Mint is great to have working out of the box but what part of "I understand" why Ubuntu chooses not to, did you not understand? Why would I go back to mint now? What does that have to do with the fact that I do not like reinstalling the same thing that I have had working with Ubuntu before and doing this upon every clean install do you not understand? Go run Mint, is not an answer. 

I do not believe distributions should leave important time wasting problems to their derivatives.

You are suggesting that the time it takes, is solely a function of the choice Ubuntu has made.  This is exactly the point I am trying to counter. 

1. We should get to a point where Ubuntu can install whatever is needed. Correct corrupt laws, whatever.

2. Baring that (as is currently the accepted Ubuntu choice) I say that adding things like DVD reading should be unbelivebly quick and simple. No matter what you say, far more so, than they are now.  Time is the factor!

3. Also, we need to give the user a (easy presented) choice between which player and the pros and cons of each of them.

4. Find-ability needs to be easier as well. The user should not HAVE to search for the basics! (I did BTW). If it degrades to a hunting expedition, then the "right" one should be easier to find. All searching can benefit by making sure the "official" working methods are found first. This all starts with the installer.
 

5. If we want to discourage anything, stop telling people to use something else, read the (whatever) manual and that they shouldn't care (or even have an angry view) about wasting time! 

I think we are past those old ways. Some just haven't figured that out yet.

---

### Post by Happy_Man on 2007-11-05
So, um.... did you actually try VLC (which can play DVD's just fine)? I can't tell from your previous posts....

---

### Post by igknighted on 2007-11-05
> **Neobuntu said:**
> What part of, I prefer Ubuntu and I now have it working in Ubuntu did you not understand? Mint is great to have working out of the box but what part of "I understand" why Ubuntu chooses not to, did you not understand? Why would I go back to mint now? What does that have to do with the fact that I do not like reinstalling the same thing that I have had working with Ubuntu before and doing this upon every clean install do you not understand? Go run Mint, is not an answer. 

I do not believe distributions should leave important time wasting problems to their derivatives.

You are suggesting that the time it takes, is solely a function of the choice Ubuntu has made.  This is exactly the point I am trying to counter. 

1. We should get to a point where Ubuntu can install whatever is needed. Correct corrupt laws, whatever.

2. Baring that (as is currently the accepted Ubuntu choice) I say that adding things like DVD reading should be unbelivebly quick and simple. No matter what you say, far more so, than they are now.  Time is the factor!

3. Also, we need to give the user a (easy presented) choice between which player and the pros and cons of each of them.

4. Find-ability needs to be easier as well. The user should not HAVE to search for the basics! (I did BTW). If it degrades to a hunting expedition, then the "right" one should be easier to find. All searching can benefit by making sure the "official" working methods are found first. This all starts with the installer.
 

5. If we want to discourage anything, stop telling people to use something else, read the (whatever) manual and that they shouldn't care (or even have an angry view) about wasting time! 

I think we are past those old ways. Some just haven't figured that out yet.

Sorry, as things stand now the legal teams of the major distro's are uncomfortable with this.  An official Ubuntu source just can't point users towards solutions of questionable legality.

All this said, I just found this article on my igoogle page (note: this is blogspam, while I think the author is raising good points, I do not for one second endorse him/her as an expert who knows more than you or I on the subject): [http://www.osweekly.com/index.php?option=com_content&task=view&id=2689&Itemid=449](http://www.osweekly.com/index.php?option=com_content&task=view&id=2689&Itemid=449)

Seems that the DVD playback might be more legal than we thought.  So hopefully someday it will become an option.

Another choice would be to use fluendo.  They are talking about creating a dvd player (for sale, after all the royalties must be paid), here is the link.  They claim a target date of 2006 though, so who knows if there is anything still going on with this: [http://www.fluendo.com/products.php?product=dvd](http://www.fluendo.com/products.php?product=dvd)

EDIT: As I said before (if you had read my post), Mint is really not a new distro.  It is an alternative installer for Ubuntu.  You use the same repos and everything.  The difference is with the art and the codecs, and a few changes in default apps.  So install the ubuntu-desktop metapackage on top of mint and you have Ubuntu with all codecs, voile.

---

### Post by rsambuca on 2007-11-05
> **zorkerz said:**
> 
Most of the packages installed with ubuntu-restricted-extras are not required for encrypted dvd playback. I would like to understand which ones are?

ubuntu-restricted-extras:

&#8728; [COLOR="Red"]gstreamer0.10-plugins-ugly[/COLOR] -> libmpeg2-4, libsidplay1, liba52-0.7.4
&#8728; gstreamer0.10-plugins-ugly-multiverse
&#8728; msttcorefonts -> cabextract
&#8728; sun-java6-jre -> sun-java-bin [binfmt-support, libstdc++5 {gcc-3.3-base}, unixodbc {odbcinst1debian1}], ia32-libs
&#8728; unrar
&#8728; gstreamer0.10-plugins-bad -> libcdaudio1, libjack0 [libfreebob0], libmms0, libsoundtouch1c2, libmpcdec3*
&#8728;[COLOR="Red"] gstreamer0.10-plugins-bad-multiverse[/COLOR] -> libfaac0 [libmp4v2-o], libfaad2-0, libmjpegtools0c2a [libquicktime1]{libavcodec1d, libavutil1d}, libx265-54, libxvidcore4,
&#8728; gstreamer0.10-ffmpeg
&#8728; liblame0
&#8728; [COLOR="Red"]libdvdread3[/COLOR] -> {libdvdcss2} suggestion
 
sorry its a convoluted structure the bulleted items are dependent on ubuntu-restricted-extras. Packages following an arrow (->) are depended on the bulleted item. And so on with [] and {}.

I guess this is uninteresting to most people but I wanted to keep track of what was being installed and hopefully find out which few i actually need.

cheers allI think the ones I highlighted in red are pretty important for DVD playback.

---

### Post by Neobuntu on 2007-11-05
You know, I hope you get that I understand and accept the Ubuntu decision to NOT include things we need; for (corrupt) legal reasons. I pray this anti-competitive situation will come to an end. Yet as I said, I know that's where we are today.

So perhaps the finer issue here is how difficult it "has" to be, to add what we want and need. I submit just because it could be extremely easy and extremely easy to find, does not mean that canonical supports it.

Yet this simply demonstrates how stupid this all has become. Where are our leaders in these matters?

I read that article that suggests its only the decrypting, that doesn't always take place that is in question and that CSS stuff is impossible to prove, thus convict. I don't know. I suppose it's about how much are we going to change; under the extortion of a law suit threat?

Isn't it obvious that this makes Ubuntu appear worse than it is, and can be? Isn't it obvious that this is anti-competitive pressure that sorely needs to be struck down before more of YOUR freedoms are abused? Isn't is obvious that time saving matters? Isn't is obvious that overall user friendliness is being slowed by this mess?

I'm so sick of this mess. Now tell me, more users don't matter? Give me a break!

The more users we can get, the more of the lies and corruption are then exposed.

---

### Post by rsambuca on 2007-11-05
> **Neobuntu said:**
> You know, I hope you get that I understand and accept the Ubuntu decision to NOT include things we need; for (corrupt) legal reasons. I pray this anti-competitive situation will come to an end. Yet as I said, I know that's where we are today.

So perhaps the finer issue here is how difficult it "has" to be, to add what we want and need. I submit just because it could be extremely easy and extremely easy to find, does not mean that canonical supports it.

Yet this simply demonstrates how stupid this all has become. Where are our leaders in these matters?

I read that article that suggests its only the decrypting, that doesn't always take place that is in question and that CSS stuff is impossible to prove, thus convict. I don't know. I suppose it's about how much are we going to change; under the extortion of a law suit threat?

Isn't it obvious that this makes Ubuntu appear worse than it is, and can be? Isn't it obvious that this is anti-competitive pressure that sorely needs to be stuck down before more of YOUR freedoms are abused? Isn't is obvious that time saving matters? Isn't is obvious that overall user friendliness is being slowed by this mess?

I'm so sick of this mess. Now tell me, more users don't matter. Give me a break!

The more users we can get, the more of the lies and corruption are then exposed.
This has been discussed ad infinitum.

Perhaps a mod can move these rants into the "Recurring Discussions" section.

---

### Post by Arthur Archnix on 2007-11-05
> **MrFSL said:**
> I find it inspiring! I just notified Honda that their whole Civic line needs to be taken back to square one. The windshield washer fluid doesn't squirt out of my brand new... oh wait... I have to fill it?

Ok, I try  to be supportive of people cuz, heck, I've been frustrated before too, but this made me laugh so hard.=D>

---

### Post by lyndaj70 on 2007-11-06
I've been reading this thread with interest....

I recall when I got my first dvd player and tried to use it in Linux (suse, in fact)...

Days and days later I finally figured out how to rip dvd's in suse, and play the ripped Dvd's, but I was never able to figure out how to play a simple store-bought DVD....

I gave up, after multiple attempts until I discovered Ubuntu in 2005 (5.04).  Within two hours I was playing DVD's!  

I know it's frustrating when things don't "just work" especially when it's the government's fault that you can't do WHAT YOU WANT WITH YOUR OWN STUFF!!!  

But you have it a lot easier than a lot of us in the earlier days of Linux, but still you have to look at it like going to a foreign country --- until you learn the right protocol on how to ask about the bathroom, you're gonna suffer :lolflag:

I now you're frustrated, and I wish it could be fixed, but right now we have to deal with it... If you think the process could be explained to new ones better, please give to the community by writing a howto on the subject.

~Lynda

---

### Post by akiratheoni on 2007-11-06
> **biomedtech said:**
> I read the FAQ that recommends waiting a month to install new releases, but I just couldn't help myself. Feisty was so kickass that I couldn't wait for Gutsy.  As far as I am concerned, Gutsy is Busted, and needs to back to the drawing board. 

I understand that some media is unsupported, but a store-bought DVD movie?  What BS. 
DVD has only been around for , what, a decade or so? It's not just one commercial DVD movie, but everyone one I've tried. I am not trying to view a Nero-burned product, just wanting to enjoy Season 10 of SG-1 on Gutsy, but instead I get this nonsense about how 'can't open .vob files'. 

Feisty did not have this problem. 

Some other quirks which I addressed in seperate posts are still problems. Items such a  clock update should not be an issue at all ( I am not a programmer, but a clock update doesn't seem like rocket science to this reporter). 

very disppointed with Gutsy, in general.  gonna have to boot into Windows to watch a store-bought DVD movie. What BS.

I'm sure you've read the replies but I just wanted to say that your condescending tone is very rude and if I were the only person in the world to give you support, I wouldn't give you any. Please lighten up and change your tone. For the good of us all. 

The reason why Gutsy can't read DVDs natively is a simple reason called 'legality'. Now, it would be better if you gave us some 'respect'.

---

### Post by moeFinley on 2007-11-06
> **akiratheoni said:**
> I'm sure you've read the replies but I just wanted to say that your condescending tone is very rude and if I were the only person in the world to give you support, I wouldn't give you any. Please lighten up and change your tone. For the good of us all. 

The reason why Gutsy can't read DVDs natively is a simple reason called 'legality'. Now, it would be better if you gave us some 'respect'.

Wow.  Everybody's feelings are obviously quite raw on this subject.

---

### Post by erginemr on 2007-11-06
> **akiratheoni said:**
> I'm sure you've read the replies but I just wanted to say that your condescending tone is very rude and if I were the only person in the world to give you support, I wouldn't give you any. Please lighten up and change your tone. For the good of us all. 

The reason why Gutsy can't read DVDs natively is a simple reason called 'legality'. Now, it would be better if you gave us some 'respect'.

+1 to that. If we are one big family as Ubuntu users, we should learn to be polite and respect each other. After all, that is the essence of the word Ubuntu.

---

### Post by statto1977 on 2008-02-22
Sorry to resurrect this thread, but a search on "region hack" revealed this was the most recent thread on the subject.

I have a dvd-rom drive that allows a specific number of region changes before locking the drive. Am I right in thinking that this isn't an issue under ubuntu? If it is an issue and the drive will lock is there anything I can do about it?

Thanks. :)

---

