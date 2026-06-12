---
title: "Seems Like This Always Happens In Linux"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by jpsimm on 2007-09-11
I use Dapper and it's great!  Really.  

But...   here's something that's happened before with other flavors and now is recurring with U.

Dapper and my Modem work perfectly.  

I installed Edgy and the modem does not work.
I installed Feisty and the modem does not work.

What's the msytery?  

How come newer versions are not as good as older?

What is the reason for this?

Here's what I did.

I installed Dapper on another HD, went online and upped it to Edgy.  This took a little more than three days during which the modem connection was flawlessly perfect.  After cleanup and restart the modem no longer dials.  There is no indication of anything wrong.  No error message.  No nothing.  It just doesn't dial.  The method of activation in Dapper was to click "activate" then it dialed right away.  In edgy the method of activation is to click the activate box.  Nothing happens after that.

This sort of thing has happend to me before.  It does not lead to good feelings for the future with Ubuntu.  I can't help it that I have to use a dialup.  It's the same old story.  Forget the folks who live in sparsely populated areas cause we can't make a profit there.

Will someone tell me how to convey this to the people who do the programming for Ubuntu, not just the helpful community members on this forum.  I want to fix it sure but I want to be told WHY by someone in authority as well.  

Stuck with Dapper in the Desert.

---

### Post by zetsumei on 2007-09-11
Get cable, it doesn't cost that much -_-

---

### Post by jpsimm on 2007-09-11
Ain't no CATV where I live amigo.  The residents are too spread out.  It's Telco Landline or nothing.

---

### Post by Dr Small on 2007-09-11
You can get satelight, which is what I have :p

Dr Small

---

### Post by zetsumei on 2007-09-11
Oh.  My bad then.  Maybe it's since it's an older hardware, that the devlopers figured no one used them no more, which I don't know why they would think that, but just my opinion.  If all else fails, you might be able to code it directly into the kernel and get it to work that way.

---

### Post by stchman on 2007-09-11
> **jpsimm said:**
> I use Dapper and it's great!  Really.  

But...   here's something that's happened before with other flavors and now is recurring with U.

Dapper and my Modem work perfectly.  

I installed Edgy and the modem does not work.
I installed Feisty and the modem does not work.

What's the msytery?  

How come newer versions are not as good as older?

What is the reason for this?

Here's what I did.

I installed Dapper on another HD, went online and upped it to Edgy.  This took a little more than three days during which the modem connection was flawlessly perfect.  After cleanup and restart the modem no longer dials.  There is no indication of anything wrong.  No error message.  No nothing.  It just doesn't dial.  The method of activation in Dapper was to click "activate" then it dialed right away.  In edgy the method of activation is to click the activate box.  Nothing happens after that.

This sort of thing has happend to me before.  It does not lead to good feelings for the future with Ubuntu.  I can't help it that I have to use a dialup.  It's the same old story.  Forget the folks who live in sparsely populated areas cause we can't make a profit there.

Will someone tell me how to convey this to the people who do the programming for Ubuntu, not just the helpful community members on this forum.  I want to fix it sure but I want to be told WHY by someone in authority as well.  

Stuck with Dapper in the Desert.

What kind of modem do you have in your PC?  Did the modem work out of the box with Dapper?  If no what did you do to get it working?

---

### Post by kellemes on 2007-09-11
I think it's more that you need to understand how to setup your modem by hand I guess..
I understand you expect your modem to simply work out of the box but this will not always be the case (as you just found out). This doesn't mean it's not supported, it obviously is.. Don't forget, most of the world population is on dialup.

---

### Post by brennydoogles on 2007-09-11
> **zetsumei said:**
> Get cable, it doesn't cost that much -_-

There are many areas of the country/world where cable doesn't even exist, let alone cable internet. We should be providing support for people all over the world, not just those who happen to live close enough to a cable company. I was recently in a part of Mexico where there was only dialup, and I was forced to use a super slow WINDOWS computer because Feisty did not play nice with my dialup modem. We should fix this.

---

### Post by jpsimm on 2007-09-11
It's a Best Data Smart One model 56spx2 and worked right outta the box with Dapper.  It was detected automaticaly and I had to do nothing but select the "activate" on the connection panel.  

Why should newer versions be less capable????????  

ps I only got the thing less than a year ago at Fry Electronics.

---

### Post by jpsimm on 2007-09-11
Brennydoogles,


Great Idea and I agree.

Do you know how to get the attention of the Ubuntu developers.  I'd like them to see my post and respond.

It's illogical don't you think????

All this stuff is man-made and is thus fixable if the right person decides to do it.  But first they (he or she) has to be prompted to do so.

Thanks

---

### Post by raijinsetsu on 2007-09-11
Run "lspci" as root, make sure the modem is still listed.
If it's listed, then it could just be that the kernel module for your modem is no longer auto-loading.
Lastly, if that's not the case, then it could be a problem with whatever program is doing the dialing for you. I have never had dial-up on a *nix machine, so I can't tell you anything about the dialer.

---

### Post by 3rr0r on 2007-09-11
1. How do you live in So. Cal and only have dial up?
2. Although it may not be the case, why don't you buy a more "linux friendly" brand modem?
3. If your modem was supported, I'm sure there it still is.  It just might not work out of the box.

---

### Post by mikewhatever on 2007-09-11
> **jpsimm said:**
> Brennydoogles,


Do you know how to get the attention of the Ubuntu developers.  I'd like them to see my post and respond.


You should file a bug report at [http://www.launchpad.net](http://www.launchpad.net). However, I am not at all sure your bug environment can be easily recreated to confirm it.

---

### Post by jpsimm on 2007-09-11
> **kellemes said:**
> I think it's more that you need to understand how to setup your modem by hand I guess..
I understand you expect your modem to simply work out of the box but this will not always be the case (as you just found out). This doesn't mean it's not supported, it obviously is.. Don't forget, most of the world population is on dialup.




Not quite right.

You should see my collection of modems amigo!!!!

I expect each newer version of Ubuntu to be an improvement over the preceeding versions.  This means, amongst other things, that a feature that works perfectly in one version should be unchanged in the newer.  The programming routines for modems which work so well in Dapper should remain unchanged in Edgy and Feisty.  Is that unreasonable???

This is plainly not the case.  I'd like an Ubuntu developer to tell me why this is so, not just how to fix it.

I have a feeling that the answer is in changes made to Debian which are incorporated into the newer Ubuntu versions.  This is why I want the developer guys to see my post.  Does anyone know how to send a post to them directly?

Thanks

---

### Post by 3rr0r on 2007-09-11
use this list to buy a new one

[http://www.linmodems.galeon.com/latest.htm](http://www.linmodems.galeon.com/latest.htm)

I did a search on the forums and it seems everyone with your brand of modem problem's went unanswered.  I say just dump the frustration, drop the $10-$20 and get one that you know will work.

Also, use this resource if you haven't already [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by 3rr0r on 2007-09-11
*******Possible Fix********

Some who went form 6.06 to 6.10 lost connectivity.  They fixed it by doing the following:

I switched from the network administrator to the command line starting the connection with the pon command.

To do this you need to write or modify two files that are in
/etc/ppp/peers/
/etc/chatscripts/

the file already present should be
/etc/ppp/peers/ppp0
/etc/chatscripts/ppp0

and

/etc/ppp/peers/provider
/etc/chatscripts/provider

you can modify one of this or write a new one.

I modified the ppp0

now they look as follow

/etc/ppp/peers/ppp0:

************************************************** ***

connect "/usr/sbin/chat -v -f /etc/chatscripts/ppp0"

usepeerdns

noauth

defaultroute

/dev/insert your modem device
user "[COLOR="Red"]telecom[/COLOR]"
115200

************************************************** ****

/etc/chatscripts/ppp0:

************************************************** ****
TIMEOUT 60
ABORT ERROR
ABORT BUSY
ABORT VOICE
ABORT "NO CARRIER"
ABORT "NO DIALTONE"
ABORT "NO DIAL TONE"
ABORT "NO ANSWER"
"" "ATZ"
"" "ATM1M0"
OK-AT-OK "[COLOR="Red"]ATDTW insert here your provider's phone number[/COLOR]"
TIMEOUT 75
CONNECT

************************************************** *****

once adapted these files I run

```
pon ppp0
```

on the command line and the pc start dialing.

Hope this can help you

regards

---

### Post by jpsimm on 2007-09-11
> **3rr0r said:**
> 1. How do you live in So. Cal and only have dial up?
2. Although it may not be the case, why don't you buy a more "linux friendly" brand modem?
3. If your modem was supported, I'm sure there it still is.  It just might not work out of the box.


1.  I live in a small desert town.  We have a store with a gas pump in front.  That's it.  No CATV.  No DSL.  Satellite for TV unless you put up an antenna and then I only get Mexican stations.  To make things worse the dorks who run internet satellites only recognize M$ and Apple, as usual.

2.  Each time I try a new flavor of Linux I have to buy a new modem it seems.  You should see my modem collection.

3.  My modem does work out of the box on Dapper but not on Edgy or Feisty.  Are those two newer versions really "improvements".  Hummmmm?

This is why I want to communicate with some Ubuntu developers.  to find out why the inconsistancies.

Thanks.

---

### Post by jpsimm on 2007-09-11
> **3rr0r said:**
> *******Possible Fix********

Some who went form 6.06 to 6.10 lost connectivity.  They fixed it by doing the following:

I switched from the network administrator to the command line starting the connection with the pon command.

To do this you need to write or modify two files that are in
/etc/ppp/peers/
/etc/chatscripts/

the file already present should be
/etc/ppp/peers/ppp0
/etc/chatscripts/ppp0

and

/etc/ppp/peers/provider
/etc/chatscripts/provider

you can modify one of this or write a new one.

I modified the ppp0

now they look as follow

/etc/ppp/peers/ppp0:

************************************************** ***

connect "/usr/sbin/chat -v -f /etc/chatscripts/ppp0"

usepeerdns

noauth

defaultroute

/dev/insert your modem device
user "[COLOR="Red"]telecom[/COLOR]"
115200

************************************************** ****

/etc/chatscripts/ppp0:

************************************************** ****
TIMEOUT 60
ABORT ERROR
ABORT BUSY
ABORT VOICE
ABORT "NO CARRIER"
ABORT "NO DIALTONE"
ABORT "NO DIAL TONE"
ABORT "NO ANSWER"
"" "ATZ"
"" "ATM1M0"
OK-AT-OK "[COLOR="Red"]ATDTW insert here your provider's phone number[/COLOR]"
TIMEOUT 75
CONNECT

************************************************** *****

once adapted these files I run

```
pon ppp0
```

on the command line and the pc start dialing.

Hope this can help you

regards





Thanks man that's worth a try.  It may fix it but it doesn't explain why newer versions are less capable than older.  This need not be so. 

I'll give it a go but remember this is the newbie forum page.  I've not done any file writting since the days of the Commodore 64 when I, like lots of others, learned basic.

Thanks

---

### Post by 3rr0r on 2007-09-11
Of the 2 pages of posts that I found on your modem, almost everyone said they coudln't get it to work.  You should have researched the modem before you bought it.  It sucks, but linux doesn't support everything right now.

That said, one guy managed to get his to work, but he had to manually enter the dns servers.  That would require you to call your ISP and get the dns address from them.  Then enter it manually (which I do not know how, perhaps in network settings).  Good luck, thats 2 things for you to try in total.

---

### Post by 3rr0r on 2007-09-11
> **jpsimm said:**
> Thanks man that's worth a try.  It may fix it but it doesn't explain why newer versions are less capable than older.  This need not be so. 

I'll give it a go but remember this is the newbie forum page.  I've not done any file writting since the days of the Commodore 64 when I, like lots of others, learned basic.

Thanks

If you really want help editing this, make sure you post output of the files before & after you edit.  You should probably copy the file before you edit it as well.

```

cp filename filename.backup
```
will make a copy of a file called file.backup

---

### Post by n3tfury on 2007-09-11
> **3rr0r said:**
> You should have researched the modem before you bought it.  It sucks, but linux doesn't support everything right now.



maybe you didn't read the first post correctly.  it worked in Dapper, and stopped working in Edgy and Feisty.

---

### Post by 3rr0r on 2007-09-11
> **n3tfury said:**
> maybe you didn't read the first post correctly.  it worked in Dapper, and stopped working in Edgy and Feisty.

I meant look for one that is compatible before upgrading...
check to see if other users are having problems with the modem before upgrading...
he said he has a collection of modems so they also do not work...?

think some ok?

---

### Post by n3tfury on 2007-09-11
> **3rr0r said:**
> I meant look for one that is compatible before upgrading...


how about *you* think some and put yourself in his shoes.  it's not a stretch to think that your modem will work in the next release when it's working just fine right now.

---

### Post by 3rr0r on 2007-09-11
> **n3tfury said:**
> how about *you* think some and put yourself in his shoes.  it's not a stretch to think that your modem will work in the next release when it's working just fine right now.

Of course... because backwards compatibility is a standard?  There's a reason caution is recommended when changing what version you run.

---

### Post by wolfen69 on 2007-09-11
another option is to just install dapper again. it's better than nothing.

---

### Post by danny joe ritchie on 2007-09-11
I've had a couple of those Best Data modems. They are supported, but you do have to set them up! 

I use an old Actiontec now but the setup is the same !

---

### Post by 3rr0r on 2007-09-11
> **danny joe ritchie said:**
> I've had a couple of those Best Data modems. They are supported, but you do have to set them up! 

I use an old Actiontec now but the setup is the same !

could you be more specific on how you went about to set them up?

---

### Post by jpsimm on 2007-09-11
> **n3tfury said:**
> maybe you didn't read the first post correctly.  it worked in Dapper, and stopped working in Edgy and Feisty.




I bought the modem before there was any such thing as Edgy or Feisty.  

As I said, it works perfectly with Dapper.  

Again, if it is so good with dapper why not Dapper's successors?   Aren't they supposed to be improvements?

Thanks

---

### Post by Terl on 2007-09-11
> **jpsimm said:**
> I bought the modem before there was any such thing as Edgy or Feisty.  

As I said, it works perfectly with Dapper.  

Again, if it is so good with dapper why not Dapper's successors?   Aren't they supposed to be improvements?

Thanks

Technically speaking, it would seem so.  But, on the other side there is a huge variety of hardware out there and many combinations possible of said hardware so, sadly, some things break.  It does not only happen in Linux either.  Even M$ leaves folks behind at times.  Look at the hardware issues with Vista.

There are also many people who still use older versions of many o/s's because of hardware issues.  I understand you being upset, though, as I have been there myself.  Is there a reason you had to upgrade?

---

### Post by BrendanM on 2007-09-11
jpsimm, I agree with you. Newer versions of Ubuntu should support hardware that worked on the last version.

If you want to get in touch with the Ubuntu developers, posting a bug report on launchpad is the way to go. They definitely read and respond to bug reports. Be sure to include as much detail as possible and mention that you're willing to help them test patches if they want.

Good luck.

---

### Post by danny joe ritchie on 2007-09-11
sorry, i changed modems; i am running a best data 56 spx2. on fiesty
left click on manual network configuration icon
then it should ask for your password
click on modem connection
then click on properties
check enable connection
enter information
next click on modem
modem port should be /dev/ttySo
check dial type
go to option
check all three buttons
It worked for me!

---

### Post by kerry_s on 2007-09-11
edgy and fiesty was a switch to the new generic kernel where the butchered the hell out of it, they naturally dropped support for the old stuff. try installing the i386 kernel.

better yet you should move to debian, they don't do that kind of crap, old stuff is still supported and there are still separate kernels for the different processors.

net, installs gnome> [http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso)
xfce4> [http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso)

the problem is your on dial up, not easy to just switch. oh well

---

### Post by danny joe ritchie on 2007-09-11
Apparently that modem will work with 6.10 too! I have my system dual booted with 6.10 and 7.04, (I'm using 6.10 now)

I used pppconfig to set it up on 6.10!

---

### Post by danny joe ritchie on 2007-09-11
> **jpsimm said:**
> It's a Best Data Smart One model 56spx2 and worked right outta the box with Dapper.  It was detected automaticaly and I had to do nothing but select the "activate" on the connection panel.  

Why should newer versions be less capable????????  

ps I only got the thing less than a year ago at Fry Electronics.

The program that connects you to the Modem has been updated, some things have been changed, but your Best Data modem works with 6.10 and 7.04!

---

### Post by jpsimm on 2007-09-11
> **3rr0r said:**
> Of course... because backwards compatibility is a standard?  There's a reason caution is recommended when changing what version you run.




Backwards?????

Since when is the latest version of ANYTHING supposed to be less capable (not as good)  than it's predecessor?

A reason caution is recommended?

This sounds like "GEEKS only".   Ordinary users need not apply...

If caution is necessary just to simply upgrade (UPGRADE)  UP UP UP as in "BETTER than the last version, not worse" then the programmers are failing the people who look to Ubuntu to be a cut above.

Sure, derive Ubuntu from Debian but be bold enough to fix it where it needs fixing.  If you do this there will be nothing else to stop Ubuntu from burying M$ in it's dust.   As it seems to be now, it is no better or worse than Xandros or Linspire of any of the rest.

If the good folks at "Linux for Humans" can't do better for us ordinary humans then Bill Gates is secure, and will remain so,  in his position as leader in the world in computing.  His Windows might be bad but damn near any modem will work with it.  Linux could be as capable.  It's just a question of doing it.

Note:

I did not lose any files or anything like that.  I installed and upgraded 6.06 to 6.10 on a spare HD just to see what would happen.  I am now back on the regular drive, having found out.

OK so I can stick with Dapper but what about when it is no longer supported? 

I refuse to go back to M$ no matter what

Let's quit this thread now before it turns into a food fight.

Thanks again to y'all.....

---

### Post by danny joe ritchie on 2007-09-11
I understand your frustration, if you need help with your modem let us know!

---

### Post by jpsimm on 2007-09-11
> **danny joe ritchie said:**
> The program that connects you to the Modem has been updated, some things have been changed, but your Best Data modem works with 6.10 and 7.04!



Apparently this is so but why can't the update import the previous version's modem specs into itself?  You know, kind of like how a new mail prg can go get your old address book.  I don't buy that it can't be done.  If it did it truly would be an upgrade and then, look out Billy G.

Someone else recommended a site with modem stuff on it but will I be able to re-write a file in Linux?
I'd better learn how and try it first on my spare HD in case the whole thing tanks big time.

Thanks

---

### Post by 3rr0r on 2007-09-11
jpsimm,

  Are you even going to try to fix your system or are you just going to post and cry about how it doesn't work out of the box?  Linux is not an operating system where everything is handed to you.  Sure, it's getting that way, which in a way is great because the user base will expand but you have to accept that on occasion it will need some tweaking.

  That said, please stop QQ'ing about how its an UPgrade and what not.  UPgrade doesn't necessarily mean they will support everything that they once did.  If you need an example of that, I will steer you to Vista.  Since you obviously misinterpreted what I said earlier, backwards compatibility means that it will support what it once did (hence compatible with stuff that is backwards meaning previous versions).  It's a great idea but it is in no way a standard or a law.  Of course it makes logical sense to expect it but that is not always the case.  Either way, it has been confirmed by another user that it does in fact work in 7.04.  

   I already posted 2 different possible solutions and you have yet to post the results for either of them.  Quit b1tch1ng and try to fix it already.  If that doesn't work, then say so.

---

### Post by danny joe ritchie on 2007-09-11
I wouldn't call it much of an improvement, but hey, if you want too get it working it's not that hard !

---

### Post by jpsimm on 2007-09-11
> **3rr0r said:**
> jpsimm,

  Are you even going to try to fix your system or are you just going to post and cry about how it doesn't work out of the box?  Linux is not an operating system where everything is handed to you.  Sure, it's getting that way, which in a way is great because the user base will expand but you have to accept that on occasion it will need some tweaking.

  That said, please stop QQ'ing about how its an UPgrade and what not.  UPgrade doesn't necessarily mean they will support everything that they once did.  If you need an example of that, I will steer you to Vista.  Since you obviously misinterpreted what I said earlier, backwards compatibility means that it will support what it once did (hence compatible with stuff that is backwards meaning previous versions).  It's a great idea but it is in no way a standard or a law.  Of course it makes logical sense to expect it but that is not always the case.  Either way, it has been confirmed by another user that it does in fact work in 7.04.  

   I already posted 2 different possible solutions and you have yet to post the results for either of them.  Quit b1tch1ng and try to fix it already.  If that doesn't work, then say so.





Solutions are one thing and I will solve the problem thanks to various helpful responses but the major concern that I have is will the developers who drop these big changes on us in such a seemingly cavalier manner without so much as a note to modem users with information on re-configuration ever get the hint and change their ways? 

Everyone who responded to my thread was helpful except for you.  You seem more inclined to bitch about my insistance that each new version should be better than the one before.  

You are correct about one thing however.  Linux flavors are apparently dependent upon the whims of Debian in their continuance but Debian does not drop support for older hardware.

I've decided to use Dapper for the time being while I study Debian.  I will move to that Linux since I have to learn to be a geek I might as well go to the source OS.

In the meanwhile if I feel like "crying" I'll damn sure do it and if you take that personally you can just go sit in your highchair and suck your thumb for all I care.  I'm sure Bill Gates would send you a "thank you" card if he knew how you supported a "limited capability" Linux.

Indeed, you seem to be a champion of mediocrity.....

---

### Post by danny joe ritchie on 2007-09-11
We tried!

---

### Post by jpsimm on 2007-09-11
> **danny joe ritchie said:**
> We tried!

Yes and I am grateful for that (except for the guy who told me to quit crying).

I still refuse to go back to "Mediocresoft".

I still wish I knew how to communicate with the guys who develop U.

---

### Post by danny joe ritchie on 2007-09-11
Good!   
 Apparently, I made a mistake and said that was running 6.10! Actually what I have is 6.06 with updated packages!

---

### Post by ieee488 on 2007-09-11
jpsimm,

I gotta agree with you on this one.

A modem that used to work in an old release that now does not work in the new releases is a pretty big deal.

I guess they assumed that dial-up isn't a big deal anymore since everyone would be on broadband. But we all know what happens with assumptions.

I think I'll just stay with Dapper.

---

### Post by jkdub on 2007-09-12
I know I'm late here but I had the exact same problem. In Edgy and Feisty I had to use wvdial to get connected and then download gnome ppp. Fortunately for me wvdial is included out of the box.

---

