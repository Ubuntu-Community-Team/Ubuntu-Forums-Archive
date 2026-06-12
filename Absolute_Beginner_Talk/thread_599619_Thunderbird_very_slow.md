---
title: "Thunderbird very slow"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Eric Weir on 2007-11-01
I'm a bit new to Ubuntu -- actully, most of the time I'm operating under Kubuntu -- and have complained previously about the degraded performance of Thunderbird on my system compared to on my Windows system. 

Everything is delayed. E.g., right-click, and you have to wait for the menu to show up. Scroll a menu, and it's similarly delayed. Then the message list bounces around in a way that makes it difficult to see where you are, or to find find anything. Likewise, when Thunderbird is running but minimized to the panel, when I maximize it the pieces of the main application window come together slowly. It always does, of course, but sometimes I wonder if it's gonna come together. 

I've tried Evolution, Kmail, and Opera. They don't behave the same way. Scrolling is immediate and precise. But there are other things that make them unnattractive. [E.g., the first time made a simple configuration change in Kmail it crashed.]

I've been using Thunderbird a couple-three years now, and I'd really like to stick with it, but this behavior is very irritating.

I assume this is not other people's experience. Any suggestions as to what might be going on? What I might do?

Thanks in advance.

---

### Post by Crafty Kisses on 2007-11-01
That's pretty weird, you should try the following:
```
top
```
You should check there and see if anything is using up a lot of resources. :)

---

### Post by Eric Weir on 2007-11-01
> **Codename said:**
> That's pretty weird, you should try the following:
```
top
```You should check there and see if anything is using up a lot of resources. :)

Something seems to be. As I say, the problem is especially severe with Thunderbird, but I sense that things generally have slowed down somewhat since I installed Ubuntu about a month ago. 

Not sure what you're suggesting I try. Is that code that's to be entered at the terminal?

Thanks,

---

### Post by speakman on 2007-12-05
Sign me up for this issue too. Comparing to Evolution, Thunderbird is really sucky. Next to broken!

EDIT: Just filed [a bug...]("https://bugs.launchpad.net/ubuntu/+source/mozilla-thunderbird/+bug/174193")

---

### Post by philinux on 2007-12-05
I have no issues with TB on my relic of a pc.

One thing to do is File then compact folders. 

When you delete a message it does not really go until you compact. If you've had a load of messages and deleted loads it can bog the thing down really bad.

---

### Post by Eric Weir on 2007-12-05
> **philinux said:**
> I have no issues with TB on my relic of a pc.

One thing to do is File then compact folders.

I've tried everything: compacting folders; installing the xpunge extension and using it regularly; recreating my profile; and unintstalling Thunderbird, deleting everything from my prfile except my mailboxes, and reinstalling Thunderbird. Iit's still VERY slow. It takes a minimum of two seconds for any action to take effect. I literally have to WAIT for messages to open after I've clicked on them in the file list.

I'm sticking with Thunderbird, however. I have too much invested in it. And I think the fundamental problem is either with my haardware setup or my Ubuntu installation. Lots of other things are slow, too, though not as slow as Thunderbird.

---

### Post by Billy_McBong on 2007-12-05
you could install [Swiftdove,]("http://sourceforge.net/project/showfiles.php?group_id=195473") its a slightly modified version of Thunderbird that runs much faster

---

### Post by philinux on 2007-12-05
> **Eric Weir said:**
> I've tried everything: compacting folders; installing the xpunge extension and using it regularly; recreating my profile; and unintstalling Thunderbird, deleting everything from my prfile except my mailboxes, and reinstalling Thunderbird.

found this...

"Slow Thunderbird e-mail open fix. I don't know the reasons why but I know this works. There is an e-mail file that gets built each time you open e-mail that is corrupted. It is: {inbox.msf}. Close Thunderbird. Find {inbox.msf} and delete it. DO NOT DELETE the file {inbox} which has no extension as it contains all of your e-mails. Open Thunderbird and a new, uncorrupted {inbox.msf} file will be created. This may take a little while the first time. To test all is well, close Thunderbird and re-open it and it should open quickly."


Every mailbox folder has a .msf file. I just tried renaming the inbox.msf to msf.bak then fired up TB and it recreates it.

My guess would be be to create a .bak for every .msf file then run TB and see if it sorts it.

---

### Post by Eric Weir on 2007-12-05
> **Billy_McBong said:**
> you could install [Swiftdove,]("http://sourceforge.net/project/showfiles.php?group_id=195473") its a slightly modified version of Thunderbird that runs much faster

Hadn't heard of it before. I've got some things that are higher priority than my Thunderbird problems at the moment. And I think I'm gonna upgrade some hardware and then upgrade to Gutsy. But I'll check out Swiftdove -- and Swiftweasel -- after that.

My real work also has some priority and I've been neglecting it in favor of fiddling with my system.

Thanks,

---

### Post by Eric Weir on 2007-12-05
> **philinux said:**
> found this...

"Slow Thunderbird e-mail open fix. I don't know the reasons why but I know this works. There is an e-mail file that gets built each time you open e-mail that is corrupted. It is: {inbox.msf}. Close Thunderbird. Find {inbox.msf} and delete it. DO NOT DELETE the file {inbox} which has no extension as it contains all of your e-mails. Open Thunderbird and a new, uncorrupted {inbox.msf} file will be created. This may take a little while the first time. To test all is well, close Thunderbird and re-open it and it should open quickly."

Forgot to mention it, but this is one of the things I've tried. I don't really know what's going on. I don't think it's Thunderbird per se. As of last weekend I have a COMPLETELY new installation of Thunderbird. The only thing carried over from the previous installation is the mailboxes. 

No improvement. Whatsoever. That fact, plus, as I said, some other "weirdnesses" of Ubuntu/Kubuntu on my system, makes me think the problem is not Thunderbird.

Appreciate the suggestion, though.

Sincerely,

---

### Post by jwood1961 on 2008-01-04
I have similar problems loading messages HTML messages in Thunderbird 2.0.0.6 on Kubuntu (both 2.04 & 2.10)

I find changing "View.Message_Body_As" from "original html" to "simple html" (or "plain text") solves the performance problem.

I have seen reports elsewhere that reverting to 2.0.0.5 restores performance also though I haven't tried this myself.

JW

---

### Post by stella2657 on 2008-01-04
hi - i had a lot of problems with firefox and thunderbird when using the eye candy program ( they just didnt get along) , try poking around the video drivers and the special effects.:)

---

### Post by Eric Weir on 2008-01-04
> **jwood1961 said:**
> I find changing "View.Message_Body_As" from "original html" to "simple html" (or "plain text") solves the performance problem.
> **stella2657 said:**
> hi - i had a lot of problems with firefox and thunderbird when using the eye candy program ( they just didnt get along) , try poking around the video drivers and the special effects.:)

Thanks, to both of you. I'll give your suggestions a try, but I'm now convinced that there's a problem somewhere in my Ubuntu installation. I first noticed it with Thunderbird, but gradually EVERYTHING has gotten incredibly slow. I've seen what other people's installations look like, i.e., how fast things happen, and mine doesn't look anything like there's. 

I'm hoping that when I finally get around to upgrading to Gutsy, which won't be till after I install a new graphics processor, everything will speed up a little. 

Thanks again,

---

### Post by speakman on 2008-03-11
I've tried TB on many different installations, and it still is very slow. Scrolling the mail list is awful. Laggy as h-ll. 

I tried to disable the Font Rendering, and it seemd a little bit faster. Can you try it?

---

### Post by Eric Weir on 2008-03-15
> **speakman said:**
> I've tried TB on many different installations, and it still is very slow. Scrolling the mail list is awful. Laggy as h-ll. 

I tried to disable the Font Rendering, and it seemd a little bit faster. Can you try it?
I'm pretty certain that the reason I'm having the experience I'm having is that my system is very slow. When I decided to try Ubuntu, I put an old 10 GB HD in a machine I wasn't using that didn't have one. I was just going to experiment. Well, I've been using Ubuntu -- actually, Kubuntu -- pretty exclusively until this past week when everything got so slow that I had to go back to my Windows system temporarily. TB is pretty speedy on it.

I'm planning to buy a new machine with Kubuntu installed within a month or so. In the interim I'm gonna move an extra HD from the Windows machine to the Ubtuntu machine and then move my /home folder from the first HD to the second HD.

Hopefully that will improve things. If it doesn't, well, I'll have a new machine pretty soon. Hopefully that will improve things. If it doesn't, well, I don't know. Look for a new email client?

Regards,

---

### Post by speakman on 2008-03-16
I'm talking about TB's being slow in general, the harddrive isn't the issue. I'm running it on a Pentium D 3GHz with 2GB RAM and fast disks, but it's still very slow. I really think it has anything to do with the font rendering/cachine mechanism. 

One way to prove that is to open up TB fullscreen, and then switch to a new (blank) virtual desktop, and then switch back again. Then you'll see how slowly TB is rerendering itself. Now try the same thing with anything else (except Mozilla softwares).

---

### Post by broomie on 2008-03-31
I had same - did as suggested above and changed to text only on opening and all was good!


paulB

---

### Post by hihihi on 2008-05-14
confirmed, i have a sony vaio intel 2duo 2ghz on ubuntu hardy 64bit and since fresh installation of hardy on this (new) laptop thunderbird is very slow as described above,
slow scrolling in message list,
long delay on right-mouse-click to call menu (1-2sec)
(i got similar issues with firefox 3.0, it is randomly awful slow in scrolling and specially in switching tabs... firefox 2.0 was just ok)

---

### Post by Eric Weir on 2008-05-14
> **hihihi said:**
> confirmed, i have a sony vaio intel 2duo 2ghz on ubuntu hardy 64bit and since fresh installation of hardy on this (new) laptop thunderbird is very slow as described above,
slow scrolling in message list,
long delay on right-mouse-click to call menu (1-2sec)

I have a bigger hard drive now and am running Xubuntu instead of Kubuntu/Ubuntu. Thunderbird performance is lousy. Painful to use. I have absolutely no problems with it on XP on a laptop. 

Somewhere between Mozilla and Ubuntu -- or is it Linux -- there's a problem. This thread confirms it for me. 

I'm gonna give Swiftdove a try. After that, I don't know what. Maybe an iMac.

Regards,

---

### Post by Eric Weir on 2008-05-30
> **Eric Weir said:**
> I'm gonna give Swiftdove a try. After that, I don't know what. Maybe an iMac.

Well, I've tried Swiftdove. The initial experience was encouraging. Within an hour so, it was behaving exactly like Thunderbird. [Actually, Firefox is as bad as Thunderbird.]

A couple weekends ago a couple of sharp guys spent a couple of hours with me and my machine, trying to diagnose what's going on. They couldn't come up with anything. One suggested I stop by a shop in the neighbordhood and see if a graphics card [in place of the onboard graphics processor] and additional memory would help. 

The guys in the shop didn't see in problem with the onboard graphics processor, so we didn't even try that option. We took out my 512 Mb of RAM and put in 2 Gb. Absolutely no difference.

I'm very wary of investing in a new machine, i.e., a custom build with Ubuntu. An iMac would be a lot of money, but I'm very tired of fiddling around and not getting any results.

---

### Post by brdokoky on 2008-06-05
When I get problem with software thinking its hardware, that I backup all and try an other system ,or in a virtual machine. That you can find problem with hardware very easy.

---

### Post by tobiasly on 2008-06-06
I can confirm this as well on a fresh install of Hardy 64-bit, with nvidia accelerated drivers. Everything else is working fine, I have Compiz enabled, Firefox scrolls fine, scrolling within a message or the folder list in Thunderbird is fine, but scrolling the message list is so slow it's unusable (and pegs CPU at 100%).

---

