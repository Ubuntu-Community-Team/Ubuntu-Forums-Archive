---
title: "Firefox font rendering post 7.10 upgrade: revert to 7.04 style"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Phil Airtime on 2007-10-19
Just a quick question which hopefully won't get buried under the masses of queries:

I'm not happy with the new font rendering in Firefox under Gutsy. 

Here's a popular website in Feisty: [http://img65.imageshack.us/img65/7342/screenshotmc8.png](http://img65.imageshack.us/img65/7342/screenshotmc8.png)
And here's the same website in Gutsy: [http://img526.imageshack.us/img526/6817/screenshotpx8.png](http://img526.imageshack.us/img526/6817/screenshotpx8.png)

I've played with the font rendering settings in Appearance, which affect the menu bars etc. but not websites in Firefox. Is there some way to get my fonts exactly how they were under Feisty? I like Gutsy, but I'd rather my fonts stayed the same; nice and soft. Georgia seems to be particularly badly-affected. 

Cheers

---

### Post by secretkeeper81 on 2007-10-19
I'm with you!
If anyone knows how to fix this, please let us know!

---

### Post by hyper_ch on 2007-10-19
actually I think in gutsy the font looks better on those screenshots

---

### Post by Phil Airtime on 2007-10-19
> **hyper_ch said:**
> actually I think in gutsy the font looks better on those screenshots

I don't. I've always preferred the way fonts are rendered on a Mac and that's how Feisty used to do them. These new ones look a bit like Windows, which I've never been keen on. Surely you can't prefer that new text to the nice, smooth Georgia on the old screenshot? 

Anyway, without wanting to sound offhand, it's not a debate on what everyone likes. *I* preferred it the old way, and that's why I'm asking how to revert it!

---

### Post by philinux on 2007-10-19
Thats exactly the reason I'm using ubuntuzilla, nice font rendering just like in feisty

---

### Post by Pierre Lourens on 2007-10-19
I'm not at a computer with Firefox right now, but I (think) I remember a setting in Firefox for aliasing.  That might help, I don't know for sure.  Sorry if there is no such setting and I'm hallucinating.. hah

---

### Post by Phil Airtime on 2007-10-19
> **philinux said:**
> Thats exactly the reason I'm using ubuntuzilla, nice font rendering just like in feisty

Brilliant, you're an absolute star. That's exactly what I wanted. Cheers!

---

### Post by Phil Airtime on 2007-10-19
I'm going to have to re-open this thread. After a reboot, the Ubuntuzilla Firefox is still the one that's in use (2.0.0.8 as opposed to the repos' 2.0.0.6) but the fonts are all miserable again. Grr. It's back to Feisty if this carries on; it might not be a big issue to some people, but I like my fonts just-so. And it makes a change from answering questions about that bloody desktop cube, no?

---

### Post by Technoviking on 2007-10-19
Goto System --> Appearance --> Fonts and play with the settings there. That may help.

---

### Post by hyper_ch on 2007-10-19
> **Phil Airtime said:**
> I'm going to have to re-open this thread. After a reboot, the Ubuntuzilla Firefox is still the one that's in use (2.0.0.8 as opposed to the repos' 2.0.0.6) but the fonts are all miserable again. Grr. It's back to Feisty if this carries on; it might not be a big issue to some people, but I like my fonts just-so. And it makes a change from answering questions about that bloody desktop cube, no?

After a while you'll get used to it...

---

### Post by Phil Airtime on 2007-10-19
> **Mike said:**
> Goto System --> Appearance --> Fonts and play with the settings there. That may help.

That alters the fonts on the menu bar and similar items, but doesn't affect how fonts are rendered in Firefox. Frustratingly, installing the official Mozilla build of Firefox via Ubuntuzilla fixed the problem, but a reboot brought it back. I'm not particularly familiar with the inner workings of Ubuntu as a distro; could something in Ubuntu be overriding Firefox settings?

> **hyper_ch said:**
> After a while you'll get used to it...

Without wanting to sound rude, that's a fairly pointless reply; I don't want to get used to it. I want my old fonts back. I'm back on Feisty for now because I really can't sit and look at those fonts for hours, but if some resolution comes I'll upgrade again. It's a shame, because there are some nice improvements in Gutsy (I was amazed when I turned on my printer and it immediately said "ready to print", for example) but the change in fonts isn't worth it.

---

### Post by Ubucat on 2007-10-19
Hi, I have to agree with you that current Firefox fonts are not looking like they were in 7.04, and I want them back.

I found this workaround **[here]("http://ubuntuforums.org/showthread.php?t=580557")**, it worked for me. Actually i had to set the Font Hinting (System->Preferences->Appearance->Fonts->Details) to "Slight" to get the best result, but "None" can work too. The default value is "Medium" and it's also the value used in 7.04 so I don't know why it changed. It may be possible to investigate the problem starting from this thing.
I hope it can help and you can get the fonts looking the way you like.

Regards

---

### Post by Pierre Lourens on 2007-10-19
I dont know if this alternative will work for you guys: 

[http://ubuntuforums.org/showthread.php?p=16896](http://ubuntuforums.org/showthread.php?p=16896)

Cheers

---

### Post by nabla on 2007-10-20
I'm with you, I prefered default font rendering from Feisty, for some reason in Gutsy firefox seems to render based on System settings, Still  haven't found how to revert back but I found that Subpixel smoothing with medium hinting is tolerable for me (for now), I've never liked/used subpixel smoothing before but seems its better now in Gutsy (for my taste). If anybody finds how to get firefox to render like before please do tell.

---

### Post by nabla on 2007-10-20
So far I switched to Opera which renders fonts much better than firefox right now, comparable to feisty firefox. Give it a try.

---

### Post by MMosley on 2007-10-21
> **Ubucat said:**
> Hi, I have to agree with you that current Firefox fonts are not looking like they were in 7.04, and I want them back.

I found this workaround **[here]("http://ubuntuforums.org/showthread.php?t=580557")**, it worked for me. Actually i had to set the Font Hinting (System->Preferences->Appearance->Fonts->Details) to "Slight" to get the best result, but "None" can work too. The default value is "Medium" and it's also the value used in 7.04 so I don't know why it changed. It may be possible to investigate the problem starting from this thing.
I hope it can help and you can get the fonts looking the way you like.

Regards

This worked for me.  I set hinting to "slight" and everything is back to normal.  Thank you!

---

### Post by neymac on 2007-10-21
> **philinux said:**
> Thats exactly the reason I'm using ubuntuzilla, nice font rendering just like in feisty

What is ubuntuzilla?

---

### Post by nanotube on 2007-10-22
> **neymac said:**
> What is ubuntuzilla?

[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

### Post by hugmenot on 2007-10-22
Hey, they determined the default settings from the result of this poll:
[http://ubuntuforums.org/showthread.php?t=555964](http://ubuntuforums.org/showthread.php?t=555964)

Note how I heavily lobbied for &#8220;Slight&#8221; in that thread. I can&#8217;t stand full either, and medium doesn&#8217;t make sense in the context of subpixel rendering. Is it really true that &#8220;medium&#8221; is the default?

---

### Post by PFilter on 2007-10-22
> **nabla said:**
> I'm with you, I prefered default font rendering from Feisty, for some reason in Gutsy firefox seems to render based on System settings, Still  haven't found how to revert back but I found that Subpixel smoothing with medium hinting is tolerable for me (for now), I've never liked/used subpixel smoothing before but seems its better now in Gutsy (for my taste). If anybody finds how to get firefox to render like before please do tell.


This did it for me, hinting to medium or slight, rather than full. Firefox looks great again.

---

### Post by Pierre Lourens on 2007-10-22
> **PFilter said:**
> This did it for me, hinting to medium or slight, rather than full. Firefox looks great again.

Same here.  Changed to subpixel and medium and it's all good.

---

### Post by cb474 on 2007-10-23
I'm baffled how changing the system font preferences is helping anybody. Changing these settings do not for me in any way change how fonts appear on web pages in Firefox.

I also liked how it looked better in Feisty (and Edgy before that). I'm still looking for a way to get fonts on web pages in Firefox to render the old way.

---

### Post by alienexplorers on 2007-10-24
Here is some Knowledge Base Items about font rendering in firefox.  It seems that since 2.0.0.0 they have been using a fot rendering pattern called cairo.
> [http://kb.mozillazine.org/Browser.display.auto_quality_min_font_size](http://kb.mozillazine.org/Browser.display.auto_quality_min_font_size)
> [http://kb.mozillazine.org/Font.alias-list](http://kb.mozillazine.org/Font.alias-list)
> [http://kb.mozillazine.org/About:config_entries](http://kb.mozillazine.org/About:config_entries)

---

### Post by cb474 on 2007-10-24
Thanks for the knowledge base articles. I couldn't really find anything in those articles that helped solve the font rendering issue.

Upgrading to the latest official Firefox install with Ubuntuzilla (which works great) or using Swiftweasel instead of Firefox gets the fonts back to a more smooth anti-aliased appearance. Although they come out smaller and more tightly spaced than they were in Firefox under Feisty.

So it's a partial solution. But I still think the font rendering looked much better overall in Ubuntu's version of Firefox under Feisty.

What happened to "if it ain't broke, don't fix it"? I have to say there are quite a few little things in terms of day to day usability that have needlessly changed with Gutsy.

---

### Post by philinux on 2007-10-24
I like the feisty look. Here's how I got it

Sys Prefs Appearance

Fonts Tab then click sub pixel smoothing (i'm using an lcd)
Then click details should show smoothing lcd but then select Hinting - none

I've also got applcation font set to Ariel.

Attached is how mine looks. you need to restart firefox too.

---

### Post by Pierre Lourens on 2007-10-24
> **philinux said:**
> I like the feisty look. Here's how I got it

Sys Prefs Appearance

Fonts Tab then click sub pixel smoothing (i'm using an lcd)
Then click details should show smoothing lcd but then select Hinting - none

I've also got applcation font set to Ariel.

Attached is how mine looks. you need to restart firefox too.

Looks good, thanks for including the example.  I'll do this when I get home :)

---

### Post by cb474 on 2007-10-24
> **philinux said:**
> I like the feisty look. Here's how I got it

Sys Prefs Appearance

Fonts Tab then click sub pixel smoothing (i'm using an lcd)
Then click details should show smoothing lcd but then select Hinting - none

I've also got applcation font set to Ariel.

Attached is how mine looks. you need to restart firefox too.

Other people have mentioned this as a possible solution above. As noted above, at least for some of us (myself included), changing the system settings for pixel smoothing and hinting does not effect the way fonts appear in Firefox, both in the menus of Firefox and in the way web pages render.

---

### Post by cb474 on 2007-10-25
Okay, I think I found a solution for Firefox.

Edit /etc/environment
> gksu gedit /etc/environment

And add the line
> MOZ_DISABLE_PANGO=0

This smooths out fonts like in Firefox with Feisty. It looks almost the same though not quite. I still think Firefox was better in Feisty, but this makes a big improvement for Gutsy.

I guess in Gutsy Pango for Firefox is disabled by default? Strangely, in Feisty doing the same thing had the opposite result. "MOZ_DISABLE_PANGO=0" made Firefox in Feisty, look like the new default Firefox in Gutsy (with very thin, unsmoothed fonts). It's beyond me why enabling Pango in Feisty would make fonts look the same way as with Pango disabled in Gutsy.

---

### Post by philinux on 2007-10-30
> **cb474 said:**
> Okay, I think I found a solution for Firefox.

Edit /etc/environment
And add the line MOZ_DISABLE_PANGO=0

This smooths out fonts like in Firefox with Feisty. It looks almost the same though not quite. I still think Firefox was better in Feisty, but this makes a big improvement for Gutsy.

I guess in Gutsy Pango for Firefox is disabled by default? Strangely, in Feisty doing the same thing had the opposite result. "MOZ_DISABLE_PANGO=0" made Firefox in Feisty, look like the new default Firefox in Gutsy (with very thin, unsmoothed fonts). It's beyond me why enabling Pango in Feisty would make fonts look the same way as with Pango disabled in Gutsy.

This cancels out my fix by the way so no good. Weird how different people are getting varied results with this.

---

### Post by steve.horsley on 2007-10-30
My fonts (in Gutsy) look the same as your screenshot for Feisty. All I did was to install the real firefox from [www.mozilla.com](www.mozilla.com) (into /opt/firefox) and to add a symlink to /opt/firefox/firefox from /usr/local/bin. The symlink ensures that all requests to start firefox use the real one not the messed-up Ubuntu one because /usr/local/bin is earlier in the path than /usr/bin so is found first. You must stop all running firefox instances before you can launch the new one though - otherwise it just re-launches the currently running one.

---

### Post by cb474 on 2007-10-31
I tried installing the real Firefox, using Ubuntuzilla, as well as trying Swiftweasel. These both resulted in even worse looking fonts and nothing like Firefox in Feisty. This was also true for me in Feisty, with the real Firefox and Swiftweasel.

The only thing that has worked for me at all is enabling Pango as I explained in my post above. Might this not all have to do with some sort of change in the freetype fonts used in Gutsy or something? I don't know much about stuff like that. But I also saw a big change in my font rendering in OOo with the upgrade to 2.3.

Anyway, I have resorted to the ultimate fix: Reverting to Feisty! :) Not really because of this font issue, it was one of the few annoying bugs in Gutsy I was able to improve enough to my liking. But there were just too many other little things like this and real bugs also. I reached my bug fixing limit.

---

### Post by nanotube on 2007-11-02
> **cb474 said:**
> 
Anyway, I have resorted to the ultimate fix: Reverting to Feisty! :) Not really because of this font issue, it was one of the few annoying bugs in Gutsy I was able to improve enough to my liking. But there were just too many other little things like this and real bugs also. I reached my bug fixing limit.

hey, out of curiosity, could you please make a list of all these bugs that bugged you? i have been thinking of whether to upgrade to gutsy from feisty, and your list of bugs would help me make the decision one way or another. thanks! :)

---

### Post by cb474 on 2007-11-02
I posted about the bugs I was experiencing with Gutsy in this thread:

[http://ubuntuforums.org/showthread.php?p=3624788#post3624788](http://ubuntuforums.org/showthread.php?p=3624788#post3624788)

You might be interested in the whole thread, since it's about problems people are having with Gutsy versus Feisty.

You can see none of the bugs I experienced were catastrophic. But they all added up to a more annoying experience in terms of how I use Ubuntu on a day to day level. And I just got tired of the hours of troubleshooting that wasn't getting me very far on most of the problems I was having.

It does seem like bugs depend on the system and how you use Ubuntu. What's bad for some seems to be good for others.

---

### Post by whiskyprajer on 2007-11-07
Gutsy dictated fonts are crap for me, too, especially pages that render "plain text" (e.g., online e-mail accounts). I've tried all these suggestions, with little success. I second the motion to revert back to 7.04 style.

---

### Post by whiskyprajer on 2007-11-14
I'm bumping this one more time, in hopes that someone has stumbled across a solution. I'm on the verge of reinstalling Feisty -- the Gutsy font-woes are quite lamentable, and extremely evasive when it comes to solutions. Again, I've played with System settings, done all the suggestions listed in the last three pages, and still some websites come out looking like this:

---

### Post by whiskyprajer on 2007-11-21
One last Gutsy issue: OooWord looks like this:

Alright - I'm reverting back to Feisty!

---

### Post by evilregis on 2007-11-21
Have you tried reinstalling Gutsy?  You've obviously got a unique problem.  Perhaps something that came about while trying to fix the problem.  Either way, nothing wrong with Feisty.

---

### Post by whiskyprajer on 2007-11-21
Yeah, I did that too. Now I've reinstalled Feisty and I STILL have the same Open Office trouble! HELP!

---

### Post by hugmenot on 2007-11-21
I think you fumbled too much with your profile. For another users account, do those squares show too?

---

### Post by whiskyprajer on 2007-11-22
Bingo. I'm once again a happy "Feisty" user -- thanks heaps!

---

### Post by hohboof on 2008-03-21
The settings you're looking for might be in ~/.fonts.conf

See: [http://advogato.org/person/wtanaka/diary/13.html](http://advogato.org/person/wtanaka/diary/13.html)

---

### Post by lolwhites on 2008-04-09
cb474 - For me, your solution worked a treat for Firefox 2.0.0.13 but Firefox 3.0b4 still renders the same awful fonts.

---

### Post by Therion on 2008-04-09
Don't know if this will satisfy anyone else, but what I do to make the fonts look better in FF is go to the Preferences menu, Fonts section and then go under the Advanced button where you can change the fonts FF uses (Serif, Non-Serif, Monospace etc.).  

This is where I set ALL the available font selections to use Verdana (not a very exciting font, I know, but it seems to render well) and set all the available font-size menus (the critical setting here being "Minimum Font Size") to use a font size of "16".  

I'm stuck behind a WinXP machine at my office, so I can't be sure about the Minimum Font Size, but I'm thinking "16" works well.  Try it and of course you can adjust to suit.  It's not a perfect solution but it seems to help.

---

