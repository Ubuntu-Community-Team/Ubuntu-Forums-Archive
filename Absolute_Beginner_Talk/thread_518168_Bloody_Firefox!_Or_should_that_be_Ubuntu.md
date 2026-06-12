---
title: "Bloody Firefox! Or should that be Ubuntu?"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by Elderlygent on 2007-08-05
I run a dual boot: XP and Feisty. Firefox runs fine on XP, but on Feisty I get these nasty little pages that occupy about half my 17in screen, in some cases with type hideously overlaid. Curiously, this doesn't happen with Opera, but Opera doesn't like my Realplayer and so I can see BBC sites perfectly well but I can't hear them. I've spent a lot of time changing fonts etc. etc. etc. But the Firefox problems remain, and the online help for that much-vaunted browser is a joke.

If I was a geek I'd probably reprogram the whole shooting match, but I'm not, and I'm beginning to wonder if Open Source is worth the hassle.

---

### Post by Pragmatist on 2007-08-05
> **Elderlygent said:**
> I run a dual boot: XP and Feisty. **Firefox runs fine on XP, but on Feisty I get these nasty little pages that occupy about half my 17in screen, in some cases with type hideously overlaid.** Curiously, this doesn't happen with Opera, but Opera doesn't like my Realplayer and so I can see BBC sites perfectly well but I can't hear them. I've spent a lot of time changing fonts etc. etc. etc. But the Firefox problems remain, and the online help for that much-vaunted browser is a joke.

If I was a geek I'd probably reprogram the whole shooting match, but I'm not, and I'm beginning to wonder if Open Source is worth the hassle.

Did you have a question?  Please give us a screenshot showing the problem.

The main thing to understand, is that we are here to help you accomplish YOUR objectives.  We are not here to convince you to use Ubuntu or Open Source Software.  In the end, Linux is not for everybody, and perhaps it is not worth your trouble.  How can we answer that for you? You need to determine that for yourself.

---

### Post by starcraft.man on 2007-08-05
> **Elderlygent said:**
> I run a dual boot: XP and Feisty. Firefox runs fine on XP, but on Feisty I get these nasty little pages that occupy about half my 17in screen, in some cases with type hideously overlaid. Curiously, this doesn't happen with Opera, but Opera doesn't like my Realplayer and so I can see BBC sites perfectly well but I can't hear them. I've spent a lot of time changing fonts etc. etc. etc. But the Firefox problems remain, and the online help for that much-vaunted browser is a joke.

If I was a geek I'd probably reprogram the whole shooting match, but I'm not, and I'm beginning to wonder if Open Source is worth the hassle.

Never had any trouble rendering pages with Firefox on Ubuntu or XP. You'll have to provide more details like requested to receive any kind of help.

As for if open source is worth your time... only you can answer that question. We don't force you to do anything or lock you in, unlike another OS I know. If you want help we are here to offer our advice, if not then return back to what you were using before. Whatever you do, be happy and want to do whatever it is.

---

### Post by sailor2001 on 2007-08-05
there are good forks of fire fox...swiftfox, swift weasel, ice weasel. take your pick and try them all......if something isn't working correctly, odds are you didn't configure it right when you installed..take your time when loading apps and read directions carefully..... enjoy the os, it's great, but you have do your part also....:)

---

### Post by Elderlygent on 2007-08-07
> **Pragmatist said:**
> Did you have a question?  Please give us a screenshot showing the problem.

The main thing to understand, is that we are here to help you accomplish YOUR objectives.  We are not here to convince you to use Ubuntu or Open Source Software.  In the end, Linux is not for everybody, and perhaps it is not worth your trouble.  How can we answer that for you? You need to determine that for yourself.

Thanks for that. Having learned how to take a screenshot I can now supply a couple (I hope)

file:///home/david/Desktop/Screenshots

If this hasn't worked you may need to explain what I should do.

Thanks

---

### Post by philinux on 2007-08-07
In the message pane look for the tools there like a paperclip - attachement or just belwo and to the right is insert image.

---

### Post by philinux on 2007-08-07
Sorry got it now, cant type fast enough to get new post LOL.

Looks like the problem I had in that the font size is too big maybe. Try View Text size reduce. If this works you can sort it permenantly in preference - content fonts.

---

### Post by Pragmatist on 2007-08-07
I'm able to see the screen shot, but the only things I see that are strange are:
1.) About an 1/4 inch is cut from the left edge of the window (instead of:

Programme 
Finder

it says:

rogramme 
inder

My guess is that this was just due to the screenshot not getting the whole screen.  Is that correct?

2.) The only other thing is that in the top-left corner "Accessibility  Help, Text Only, etc..." is messed up.

Is there something else that I'm missing?  Do you this exact type of problem with every web page you visit?  How long have been using firefox?  Have you made any changes to firefox's settings?

---

### Post by Elderlygent on 2007-08-08
Thanks for that. What happens is that text gets overlaid. It should be visible down the page on the left. The same thing happens with the BBC's Radio Five Live site, which is very crowded anyway, and with The Times site.

I've been using Firefox  with XP for several years and never had a problem. My experience with it via Ubuntu is only a few weeks, as you've no doubt gathered. I thought it might be font size, but changing that doesn't help (and I can't read the text then anyway)

In general, Firefox seems to deliver a much narrower panel in Ubuntu than in XP, where it spreads itself in a very satisfactory manner.

The Firefox version I'm using in Ubuntu is 2. whatever (I upodated it about three weeks ago) so it's not some superannuated programme.l

Anyway, let me say I am very grateful for your interest. I am keen to make a success of my Ubuntu experiment, but got very frustrated after fiddling around with Firefox for a couple of weeks or so.

---

### Post by philinux on 2007-08-08
Out of interest what screen resolution are you using. I get a very narrow panel at my highest which is why I have mine set to 1024x768 this gives me exactly same "spread" of web page as I'm used to. I then adjusted the fonts to get my preference.

---

### Post by skymera on 2007-08-08
id guess at font.
look at the size of it! mahoosive.

resize thar and it should be fine :)

---

### Post by Pragmatist on 2007-08-08
Edit:  The below instructions can be helpful with similar problems, but after testing some more, the checkbox makes no difference for the BBC website.  If I switch my default font in firefox from 16 to 20, I get the same effects you are experiencing. btw, my screen resolution is 1024x768  Checking the box as I describe below, will help with many websites, but in this case the problem is definitely your font size, just like skymera pointed out.

I was able to replicate your problem.  This should solve it:

In firefox, go to:
**Edit**-->**Preferences**  
Go to "**Content**"
In the second box, titled "**Fonts and Colors**", click "**Advanced**"
Then _check the box_ that says, "***Allow pages to choose their own fonts, instead of my selections above***"

---

### Post by Elderlygent on 2007-08-09
Thanks for your perseverence. I've tried all the above suggestions and it's true that reducing the font size help--up to a point! But there are still overlays, even when I've gone down to 9pt!! I probably do need stronger glasses for the computer but that, as they say, is ridiculous. One should be able to use 14-16pt without a problem, no?

Changing the screen res. doesn't seem to make any difference at all.

I'm thinking of going over to another browser. Since Safari still isn't available for Ubuntu (is it?) this would mean Opera whic, as I said in my original post, doesn't seem to like BBC streaming radio. But mayhap there's a simple way around that.

Cheers and thanks again

---

### Post by kostkon on 2007-08-09
This is strange, it looks like a font problem, but I'm not sure. For me, the page renders perfectly as you can see from the screenshot. I have to point out that I use the Microsoft fonts.

---

### Post by kostkon on 2007-08-09
I think maybe you have a *DPI* problem! That's why the different font sizes you tried look wrong to you, compared to Windows I assume.

Could you tell us what is your resolution. Also, could you go to **System -> Preferences -> Font -> Details...** and see at the upper left corner of the window what *DPI* your system is supposed to use?

---

### Post by Elderlygent on 2007-08-09
Thanks for that. The screen res I'm using is 1024x768, not that changing it makes any difference!

I have a problem doing what you suggest about the DPI. When I go to the Content panel in Firefox's Preferences all I can see is;


Fonts and Colors, and on the right: ADVANCED and Colors. Nothing about details. Perhaps I'm in the wrong place.

I downloaded basic MS fonts and have specified Times New Roman as my default font.

I've also checked the button to allow pages to display as they are set up.

Thanks again.

David N

---

### Post by Elderlygent on 2007-08-09
OK I've found the right place. It's 105 DPI.

Cheers

---

### Post by Pragmatist on 2007-08-09
> **Elderlygent said:**
> 
I have a problem doing what you suggest about the DPI. When I go to the Content panel in Firefox's Preferences....Perhaps I'm in the wrong place.

He meant to go to system menu found on your top panel.  Your top panel should have these menus, from left to right:
Applications  Places  **System**
So you start with the System menu:
[B]System -> Preferences -> Font -> Details

[/B]Edit: In other words, you are not changing anything inside firefox.  You can have firefox closed when you do this.

---

### Post by Pragmatist on 2007-08-09
> **Elderlygent said:**
> OK I've found the right place. It's 105 DPI.

Cheers
My resolution is 1024x768 and my DPI is 96

I don't think DPI is the real issue.  My suggestion is to try firefox with default values.

1.) Close firefox and open a terminal
2.) backup your user settings folder for firefox (.mozilla):
```
cp -rf $HOME/.mozilla $HOME/backup.mozilla
```3.) move the .mozilla folder:
```
mv $HOME/.mozilla $HOME/original.mozilla
```Now start firefox and try out the troublesome web page.

Edit:  When you start firefox this time, check to see if your bookmarks are there.  If they are NOT there, then you performed the steps correctly.  Do not worry, you still have your bookmarks in the backup we made.

---

### Post by Elderlygent on 2007-08-09
Thanks, I'll have a go tomorrow.

---

### Post by stchman on 2007-08-09
> **Elderlygent said:**
> I run a dual boot: XP and Feisty. Firefox runs fine on XP, but on Feisty I get these nasty little pages that occupy about half my 17in screen, in some cases with type hideously overlaid. Curiously, this doesn't happen with Opera, but Opera doesn't like my Realplayer and so I can see BBC sites perfectly well but I can't hear them. I've spent a lot of time changing fonts etc. etc. etc. But the Firefox problems remain, and the online help for that much-vaunted browser is a joke.

If I was a geek I'd probably reprogram the whole shooting match, but I'm not, and I'm beginning to wonder if Open Source is worth the hassle.

I have near zero problems with Firefox.  I surf many sites.  The only thing I complain is that Flash 9 for linux is buggy and Adobe won't fix it.

---

### Post by Elderlygent on 2007-08-10
Well, that's fine--except that I can hardly see the text! But I guess I can home in on a detail and then enlarge that. Or get new glasses.

Many thanks anyway for your patience.

Cheers

---

### Post by ramjet_1953 on 2007-08-10
The problem is definitely the size of the font.

I can duplicate the problem by opening the same website and then clicking on [COLOR="Blue"] View>Text Size>Increase[/COLOR] button a couple of times.

I suggest that you let Firefox determine the suitable text size,, as was mentioned earlier.

Regards,
Roger :cool:

---

### Post by Pragmatist on 2007-08-10
One more, slightly tangential, point.  If the website in question followed standards-based design, you wouldn't have this problem.  In standards-based design, increasing the size of the font should not break the page design.

Unfortunately, the majority of websites currently do NOT follow standards-based design.  This is a shame because designing with standards provides, among other things, accessibility.  For instance, can you view the website with a text browser?  How about with non-visual browsers that are used by the blind?  Then there are embedded devices such as cellphones and PDAs; both of these require special design in order to be read with small screens.  And the list goes on.

As I said, this is somewhat tangential, because you said you can view this very same website with other browsers.  The BBC site is still broken since I can't increase the font without it screwing up the design.

---

### Post by Elderlygent on 2007-08-10
All very true. But I AM grateful for your patient help. I've learned a few things and I hope our paths cross 
again

Sincerely,

David N

---

