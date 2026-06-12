---
title: "Upgraded to 8.04 this morning..."
date: 2008-04-28
forum: Alabama Team - US
---

### Post by MerlinsLair on 2008-04-28
And frankly, I'm disappointed that they dumped Firefox 3 Beta on us without giving us a choice. It lacks plugin compatibility (at least for the ones I use most often) and asks for feedback for testing? WTH?! I recall LTS being Long Term Stable. Not Beta or a platform for testing a 3rd party's application! 

I hope I can get 2.0.14 back because until 3 gets stable, it's history. I needed those plugins to keep bookmarks and other stuff synced with my other machines.

The upgrade went pretty good however, so that wasn't a bust there. I downloaded an .iso first just in case, and then let the system upgrade itself. Figured if there was going to be a glitch or problem somewhere I'd at least have the .iso file for backup.

Only real glitch that I ran into was the loss of sound after the upgrade. A quick search of the main forums brought that back though.

All in all, upgrade went well but I'm leaving the jury out for the time being until I see just what all this latest version has to offer that makes it better than 7.10.

---

### Post by MerlinsLair on 2008-04-28
Well, got rid of Firefox 3 beta and installed Firefox 2 again but now I can't install any of my preferred addons. This is beginning to look like I may be going back to 7.10 before long if this keeps up. 

Anyone else experiencing issues with Firefox?

---

### Post by crane on 2008-04-28
I was planning on installing the older version of Firefox as well. I too am shocked that they have this with a beta program in it. Man do i need my gbookmarks back.
How did you install the older version of FF? Are you still gettin gth e"not compatible" message when trying to install plug-ins? Have you tried deleting or renaming the .mozilla file in your home directory? That may clear the issue.

---

### Post by Eutaw on 2008-04-28
I upgraded today. It kept everything I had, but I don't use that many plugins. It did resolve an issue I was having with playing DVDs, so I'm happy so far.

---

### Post by myusername on 2008-04-28
there is a how to on how to do this somewhere in the howto thread wow i didnt mean to say how to thatmany times lol

---

### Post by crane on 2008-04-29
OK, it's late and I am tired but here is what I did.
I downloaded [Firefox2]("http://www.mozilla.com/en-US/firefox/"). The extracted that into the /opt file.
 Then I created a shortcut on my upper panel.
Right click>add to panel then click custom launcher.
Type: Application
Name: Firefox2
command:  /opt/firefox/firefox
Comment: ForeFox 2.0.0.14
You can click the icon button (looks like a platform on a spring.
The navigate to the icon at  /opt/firefox/chrome/icons/default/default.xpm
Do not start it yet.

Next, go to your home folder. and hit ctrl+h (show's hidden files) now just rename the file .mozilla to something else by right clicking it and selecting rename. I named mine .mozilla3.
 Now start Firefox from the icon you just started. then you should be able to install your extensions. The only trouble I see is when you click links in email or maybe irc and select open in browser, I think this will open in Firefox3.
 I will post when I test it tomorrow.

---

### Post by MerlinsLair on 2008-04-29
> **crane said:**
> I was planning on installing the older version of Firefox as well. I too am shocked that they have this with a beta program in it. Man do i need my gbookmarks back.
How did you install the older version of FF? Are you still gettin gth e"not compatible" message when trying to install plug-ins? Have you tried deleting or renaming the .mozilla file in your home directory? That may clear the issue.

I uninstalled FF3 via Synaptic (took 2 tries to get rid of it too) and then installed FF2 the same way. Still can't use any of my plugins. Keep getting some infernal error message when it tries to install any of them.

I'm going to try uninstalling FF2 via Synaptic and just install it right from the Firefox site itself to see if that will help. This time I'm going to wipe all traces of it from the home directory to see if it makes any difference.

This is beginning to NOT look like an UP-grade. Don't remember signing up for "test-dummy" service on this version.

---

### Post by MerlinsLair on 2008-04-29
OK, got FF2 installed like you did Crane except I couldn't get the folder to copy over or ectract into the /opt folder. It's in my Home folder for now. Everything else is just like you said when you signed off last night...no links work from email anymore...not even FF3 tries to load. Small inconvenience but I can live with it for now. At least I got my plugins back.

Am going to do a little research on the main forums this morning to see if anyone has come up with another solution. Never can tell.

---

### Post by FredB on 2008-04-29
Don't you have read the release notes about firefox 3 being set by default instead of Firefox 2 ? :)

Anyway, before getting my *ss kicked, just think about having a firefox version which support is dead by next december in a 3 years SUPPORT distro ?

And at least, for your info, S = Support, not Stable in LTS.

---

### Post by crane on 2008-04-29
> **MerlinsLair said:**
> OK, got FF2 installed like you did Crane except I couldn't get the folder to copy over or ectract into the /opt folder. It's in my Home folder for now. Everything else is just like you said when you signed off last night...no links work from email anymore...not even FF3 tries to load. Small inconvenience but I can live with it for now. At least I got my plugins back.

Am going to do a little research on the main forums this morning to see if anyone has come up with another solution. Never can tell.

You will have to use sudo to move the file to op. Sorry I should have mentioned that. I did not uninstall Firefox 3 though. I left it and will test it out today as far as links form irc and email.
Just as a note I had to install libstdc++5 in order for Firfox2 to work.

---

### Post by crane on 2008-04-29
> **FredB said:**
> Don't you have read the release notes about firefox 3 being set by default instead of Firefox 2 ? :)

Anyway, before getting my *ss kicked, just think about having a firefox version which support is dead by next december in a 3 years SUPPORT distro ?

And at least, for your info, S = Support, not Stable in LTS.

Having it supported is fine. The problem is that people have become attached to their extensions and plug-ins as I have. None of which, at this time work under FF3. So I understand why people want FF2 back.

 ON a side note, it seems to me that FF2 has a crisper look. The fonts on FF3 are a bit blurry to me.

---

### Post by MerlinsLair on 2008-04-29
> **FredB said:**
> Don't you have read the release notes about firefox 3 being set by default instead of Firefox 2 ? :)

Anyway, before getting my *ss kicked, just think about having a firefox version which support is dead by next december in a 3 years SUPPORT distro ?

And at least, for your info, S = Support, not Stable in LTS.

Thanks for the tip there Fred. Glad you could visit our little corner of the forums here to point that out for me. That being said, I'll point out something for you sir:

1) Why install a beta version of a browser that was working just fine as a "Stable Release" as 2.0.0.14? Wait until FF3 goes Stable, then release it like all the versions before it. Reeks of M/$ tactics to me. My opinion there bud.

2) When the FF version does become outdated and support drops, THEN release FF3 for public use. NOT with a LTS version of an OS! That's absurd. Nothing works with it. What were we to do? Just blindly follow along with the game? Again, reeks of the stuff M/$ does. My opinion again bud.

3) Stable/Support to me and many others means the same thing...ready for public use as a Stable OS that's Supported by it's developers.

I use Linux for many reasons. Open Source which contributes to the developers who work hard to come out with the apps and stuff that we all use daily, Security in not having to worry near as much about what gremlin will infiltrate my system next, Ease of use with most all of the apps, programs and general offerings that come with the system itself, and more reasons than I have the time or space to add at this time.

Now, if you have any other words of wisdom that are constructive to the OP, fine. If not, well, you get my drift don't you? :roll:

No wonder so many folks still shy away from Linux with the holier-than-thou attitudes of people like you.

---

### Post by crane on 2008-04-29
LOL, nicely said. I felt he was being a bit demeaning in the way he "spoke" but I wasn't sure if it was just me. I think screaming long term support was a bit odd. Long term support to me would mean pretty much what you stated. It  software goes obsolete during the support cycle then Ubuntu would support the upgrade and push it down to the OS.

---

### Post by MerlinsLair on 2008-04-30
I don't normally tend to go off like that but for him? I felt like accommodating.

I think a Beta version of anything should be an option, not an addon to an OS that will surely have it's own bugs to contend with. Evidently, I'm not alone in this way of thinking as others are saying the same lately.

---

### Post by cyberdork33 on 2008-05-02
while I agree somewhat with the fact that something such as the default browser shouldn't be beta, I think you might have been a little harsh. I didn't see his comment as an attack or anything... and there is a big difference between "support" and "stable" You can support beta (usually not considered "stable") software... look at gmail.

That said, I haven't had many issues with FF3 for awhile, but I use a beta of foxmarks to sync my bookmarks and I really don't have many other addons (other than Adblock)

---

### Post by MerlinsLair on 2008-05-02
A difference of opinion then, I suppose. Either way, he came off to me as condescending and I replied back as "nicely" as possible. 

I'm still learning Linux and Ubuntu and didn't take too kindly to his post. Evidently, he was a bit doubtful in it too as he said, and I quote: 
> Anyway, before getting my *ss kicked, just think about having a firefox version which support is dead by next december in a 3 years SUPPORT distro ?

---

### Post by MerlinsLair on 2008-05-04
After a clean install things are looking much better now. Still using FF2 to be able to keep my plugins and so on working. When they get FF3 stable, I'll consider switching to it next. But, for now I'll keep what's working for me.

---

### Post by retrow on 2008-05-06
There was quite an uproar among folks who had voluntarily installed Hardy as early as Feb when it was still in its Alpha stages. When I got alpha 2, FF3.0b3 was default. FF3 crashes were so frequent during alpha days that the bug report portal became unusable due to the traffic of people reporting/checking the bugs.

Apart from a few glitches (like choking on flash media), FF3 is actually quite efficient as compared to FF2 and it has far better compatibility with w3c standards. It scores some 15+ points more than FF2 on Acid3 test.

Taking a philosophical view on the issue, it seems that by upgrading/installing 8.04 we take on the challenge to test-drive the upcoming Mozilla browser among other things. LTS is supposed to work outta box, be stable, et al. but considering it is LTS, the upcoming 8.04.1 will have things patched up and it will still be at the very beginning of the life cycle of Hardy.

---

### Post by tryxl on 2008-05-07
As a tech support guy, I may can shed some light on the Firefox issue.

A long term support version of a distribution should include software that is expected to be supported by the individual developers of that software for the term of the expected support.

Firefox 3 was also included due to some security issues in Firefox 2. Those issues are more critical in a windows environment than Linux, but they are still there.

All that being said, I understand the frustration of having a beta version of software forced on you without your consent. I do not know precisely why the developers included it, but I suspect my reasons are similar to theirs.

As far as the plug in issues... good luck.... I am having problems with them in FF3 as well. One solution that has helped me is that I run IE in wine. some sites are much more friendly to IE than FF. I disagre with this method f web deisgn, I think sites should be completely browser neutral, but that is not always the case.

Other upgrade issues--- be careful if you are running envy in 7.X, it causes issues in the upgrade, be certain to use the envy tool to remove your drivers then completely remove envy from your machine before the upgrade. Failure to do so has hosed 3 machines for us at my office. completely removing Envy though has allowed 4 successful upgrades.

---

### Post by MerlinsLair on 2008-05-07
I've gotten FF2 to work flawlessly now since reinstalling 8.04 from scratch as a clean install. The upgrade route just didn't work out too well for me this time. FF2 will now open from a clicked link in an email again (such as the one I got when this post was updated) and all my plugins/addons are working as before too.

FF3b is sitting there still until the dev's get the bugs out of it. I'll give it a try then. 8^)

---

### Post by llirium on 2008-05-07
> **MerlinsLair said:**
> Only real glitch that I ran into was the loss of sound after the upgrade. A quick search of the main forums brought that back though.

I'm having the same problem, could you please show me who helped you or how you fixed it?

Thanks in advance, and sorry for posting something off-topic here.  But I'm at my wits end with trying to figure this out. :/

---

### Post by MerlinsLair on 2008-05-07
No problem...it is a permissions issue. I'm gonna get killed for this but 8.04 is "sorta" like Vista now in that you (as an Admin) may have to give your self the permission to edit any file/folder on your system now.

That being said, go to ***System > Administration > Users and Groups***. When that loads, you should see a box with your name and root in it. Click once on your name then click ***Properties***. Navigate to ***User Privileges*** and take note of the options. I checked off all of them for me here.

Next, click OK and click on ***root***. Nothing may happen now and you may need to*** "Unlock"*** it. If so, click ***Unlock*** and enter your root password. Now click on ***root*** and then ***Properties > User Privileges*** and make the same selections here as you did as before making sure that the ***Use Audio Devices*** option is also checked. Click OK to close and Close once again.

You should now be able to hear sound when the system beeps or anything else. This is what I did and it worked great.

Now, I'm going to go duck for cover before someone tries to nail me for my Vista comparison. 8^)

---

### Post by fredfjr on 2008-05-12
Well, I finally pulled the trigger on 8.04 this morning...

I'd say that it's mostly gone very well.  Unlike 7.10 my ATI video card is working well!  The proprietary driver loaded without a problem and I can run at a decent resolution on my 19" monitor now (1600x1200 now vs. the 1280x1024 that I had run under 7.10).  Updated versions of apps are nice, too.

I did notice one odd thing...I tested out my video playback by playing one of the trailers I had from World of Warcraft.  It worked fine until I expanded it to full-screen where I then saw some chugging of the video.  This didn't happen on 7.10 and I could play full-screen videos with no problem back when I used Windows XP on this box.  I'm will to bet it might be an issue with Pulseaudio but I'm going to do more research before I try to place some concrete blame.

---

### Post by fredfjr on 2008-05-13
Update about my video playback experiences...

Well, Pulseaudio likely wasn't the culprit of the problems I mentioned in my previous post.  It seems to be Compiz that was the source...I disabled desktop effects and the problems disappeared for the most part.

Guess my system is starting to show its age...

---

### Post by cyberdork33 on 2008-05-13
> **fredfjr said:**
> Well, Pulseaudio likely wasn't the culprit of the problems I mentioned in my previous post.  It seems to be Compiz that was the source...I disabled desktop effects and the problems disappeared for the most part.
There are some interesting problems with Compiz and video in general, and OpenGL applications. It is not necessarily performance related.

---

