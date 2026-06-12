---
title: "Missing text / weird formatting in Firefox"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by inverseroom on 2008-02-09
OK, I posted about this once before but got no good answers...I've tried all different text smoothing options, changed fonts,changed font colors, changed desktop themes, etc....no joy.  Below is a screenshot of Firefox open on my desktop--the web page displayed is a blog my wife and I write.  The title bar should read WARD SIX, and the text below it should fill the whole line.  You'll also notice in the first post, half the date is gone.  These bits of missing text are all over the place.

When you highlight the text, it all appears again.  Then, if you navigate away and come back, it's gone.  I also see this on various forums...when I am reading a post, the text is formatted weird, characters are invisible, etc...highlighting the text fixes it...leaving and coming back restores the problem.

It's driving me bananas.  Obviously Firefox is formatting text strangely on certain types of sites...but I can find no option to change this.  I'm using FF3, but it's the same with FF2.  Konqueror works, but I like FF.  Help!

[IMG]http://inverseroom.creotia.com/pictures/screenshot.png[/IMG]

---

### Post by tibellus on 2008-02-09
Hello. Have you tried with Epiphany to see if it does the same thing? I found out that there are some tricks with highlighting in Firefox. For example, a skilled - or not so skilled, I don't know how much you need to know to do that - coder can make text on a webpage to look different when it is highlighted. I found one that when you highlighted the text, a image with Google appeared. Anyway, Epiphany uses some Firefox components. I think you should try it to see if the problems are browser-related or system-related.

Let me know what happens next. :)

---

### Post by inverseroom on 2008-02-09
I don't think it's the text highlighting issue you're referring to.  Highlighting the text is the only way to get it to look normal--it's messed up when it ISN'T highlighted.

Downloading epiphany now...

---

### Post by inverseroom on 2008-02-09
OK, text does NOT format properly in Epiphany.

---

### Post by tibellus on 2008-02-09
I am thinking about this thing: Epiphany and Firefox use Gecko, while Konqueror uses KHTML. The engine might be the problem... but why does this happen? (rhetorical question) I'll look around  try to find a solution.

---

### Post by inverseroom on 2008-02-09
Thank you!  I should add that this is only an issue in the Linux version of FF, not the Windows one.

---

### Post by tibellus on 2008-02-09
hmm, I went on your blog, using both Epiphany and Firefox and they both work well. I am searching for something that might get connected to font rendering, styles and stuff like that. You're missing a library, that's for sure, and I don't know why this happens all over the Linux world... A program should come with all its required packages.

---

### Post by tibellus on 2008-02-09
[http://forums.mozillazine.org/viewtopic.php?t=619955&sid=9591065c0181cb8f4c846057f6f67c0e](http://forums.mozillazine.org/viewtopic.php?t=619955&sid=9591065c0181cb8f4c846057f6f67c0e) This is a good starting point, I think. I don't know if it's something too relevant, but try it with Swiftfox, maybe things will work then.

---

### Post by inverseroom on 2008-02-09
> **tibellus said:**
> hmm, I went on your blog, using both Epiphany and Firefox and they both work well. I am searching for something that might get connected to font rendering, styles and stuff like that. You're missing a library, that's for sure, and I don't know why this happens all over the Linux world... A program should come with all its required packages.

I appreciate your investigating this for me.  Are there any common libraries I might not have?  There was a period when I installed and uninstalled a few things while settling on a version of FF to use...perhaps I inadvertently removed some kind of style library.  I do have the ms fonts package.

---

### Post by tibellus on 2008-02-09
I think you should have libcairo and libcairo2-dev installed. I'm not sure about this, but as far as I know this is used by Firefox.

---

### Post by inverseroom on 2008-02-09
Neither of those libraries were installed!  So I installed them...and still nothing.  I tried running "--enable-system-cairo" as that thread suggested but it didn't recognize the command....what am I missing?

---

### Post by tibellus on 2008-02-09
what about firefox-gnome-support and firefox-dev? do you have those?

---

### Post by inverseroom on 2008-02-09
No, I didn't.  Downloading now.

I must have inadvertently erased a bunch of stuff...

UPDATE nope, didn't change a thing...

---

### Post by tibellus on 2008-02-09
Hmm, I'll try to find more about this problem. It seems to strictly relate to Firefox and Epiphany, because of common elements in them. I'll ask around and see what I can find about it. I will also look for some style-related libraries. I was thinking - this might be stupid - but have you tried running firefox from console and see what errors appear when you access your site? Some messages might show up if something's wrong, but I'm not sure about this.
[COLOR="Red"]
Update:[/COLOR] Similar things are happening to me at this moment, some buttons are looking weird. The quote button is just a black rectangle. Also, on the desktop the network icon has a black square around it.

---

### Post by badmedic on 2008-02-09
The issue could have to do with your install of MS fonts as well. Maybe try removing those and see if you are still having the issue?

---

### Post by badmedic on 2008-02-09
Also... are you seeing this issue on other sites or just your blog header? There may be an issue in your blog's CSS that might be causing FF to "freak out" a little. Both your header H1 and description CSS appear to have redundant "normal" values in the font parameters. See the following:

> #header h1 {margin:5px 5px 0;padding:15px 20px .25em;line-height:1.2em;text-transform:uppercase;letter-spacing:.2em;font: **normal normal** 200% Georgia, Serif;}

#header .description {margin:0 5px 5px;padding:0 20px 15px;text-transform:uppercase;letter-spacing:.2em;line-height: 1.4em;font: **normal normal** 78% 'Trebuchet MS', Trebuchet, Arial, Verdana, Sans-serif;color: #4c4c4c;}

I am not a complete CSS expert, but I don't think having it twice like that is right.

---

### Post by tibellus on 2008-02-09
@badmedic: i don't think is something related to CSS, because it works on Konqueror, and it also works on Firefox and Epiphany on my computer.

---

### Post by badmedic on 2008-02-09
I agree that CSS is not likely to be the issue... just looking at all avenues, and there is a slight chance that it is a browser/version specific quirk.  :)

---

### Post by inverseroom on 2008-02-09
Thanks, badmedic...no, it's not just the blog...it's in lots of places, not just blogger either.

So on the recommendation of some places I found in a search, I created a .mozconfig and stuck it in the .mozilla folder with ac_add_options --enable-system-cairo in it.  That didn't work either. :(

Puzzling and annoying.

---

### Post by inverseroom on 2008-02-09
Oh, wait...you're supposed to build FF using the mozconfig...not sure how to go about this...

---

### Post by tibellus on 2008-02-09
you've built firefox from sources?

---

### Post by inverseroom on 2008-02-09
> **tibellus said:**
> you've built firefox from sources?

The fact that I have no freaking idea what that sentence means, tells you how totally in the dark I am on this subject. :confused:

Alls I want is the super special secret line of code that will make everything OK!

---

### Post by badmedic on 2008-02-09
I just realized you said you are using FireFox 3... which is still in beta. Can you tell us the exact version you have and the process/instructions you used to install it?

---

### Post by inverseroom on 2008-02-09
> **badmedic said:**
> I just realized you said you are using FireFox 3... which is still in beta. Can you tell us the exact version you have and the process/instructions you used to install it?

I just d/l'ed it via the repos, v3.0a8.  The problem is exactly the same in FF2, however.  I only got FF3 to see if this problem would be fixed in it...it wasn't, but a lot of other stuff is way better.

---

### Post by badmedic on 2008-02-09
OK... so you had the same issue before 3. Just making sure it's not an issue with the beta.

Did you ever try removing the MS fonts? It could be those are damaged/corrupted.

edit:
As a quick check, you can go to 'Preferences > Content > Fonts and Colors - Advanced' and uncheck "Allow pages to choose their oen fonts, instead of my selections above.
Then make sure all your preseleced fonts on that same area are set to generic fonts like Serif, sans-serif, or monospace.

This should stop FF from trying to use MS fonts like "Trebuchet MS" declared in the page CSS.

---

### Post by inverseroom on 2008-02-09
Yep, I already had those content settings.  I also uninstalled and reinstalled the MS core fonts (Tahoma is in fact my screen font of choice, so I would like to keep them).  Still the same problem!

---

### Post by inverseroom on 2008-02-10
Sorry to come dragging this back to the top, but I'm wondering if anyone has any other ideas?  It's such a peculiar problem...

---

### Post by badmedic on 2008-02-10
Coincidence of coincidences!.... I was just looking at the thread to see if you found a solution. :)

I searched for Firefox dependencies and came up with this list from a post over at linuxforums.org... It is for 1.5 so it is outdated, but it might point you in the right direction if a missing dependency is the issue:

> Depends: fontconfig, psmisc, debianutils (>= 1.16), libatk1.0-0 (>= 1.9.0), libc6 (>= 2.3.4-1), libcairo2 (>= 1.0.2-2), libfontconfig1 (>= 2.3.0), libfreetype6 (>= 2.1.10-1), libgcc1 (>= 1:4.0.2), libglib2.0-0 (>= 2.10.0), libgtk2.0-0 (>= 2.8.0), libidl0, libjpeg62, libpango1.0-0 (>= 1.12.1), libpng12-0 (>= 1.2.8rel), libstdc++6 (>= 4.0.2-4), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3, libxft2 (>> 2.1.1), libxi6, libxinerama1, libxrandr2, libxrender1, libxt6, zlib1g (>= 1:1.2.1), libnspr4 (>= 2:1.firefox1.5.dfsg+1.5.0.1-1ubuntu12), libnss3 (>= 2:1.firefox1.5.dfsg+1.5.0.1-1ubuntu12)

The post also lists how to look up dependencies for any package. You can read it here:
[http://www.linuxforums.org/forum/ubuntu-help/63633-command-see-dependencies-package-ubuntu.html](http://www.linuxforums.org/forum/ubuntu-help/63633-command-see-dependencies-package-ubuntu.html)

Sorry it's not a solution, but I hope it helps!

---

### Post by inverseroom on 2008-02-10
Thanks again!  I tried installing all of those...already have all the latest versions. :confused:

I really appreciate your trying to solve this one with me!

---

### Post by badmedic on 2008-02-10
Just out of curiosity... are you running Desktop Effects (Compiz Fusion)? If so, maybe try disabling all desktop effects and see if it's still happening? 

Something must be interfering with the browsers font rendering and I can't think of anything else.

---

### Post by inverseroom on 2008-02-10
Nope, I'm running no desktop effects at all...my desktop looks like Windows 95 :)

---

### Post by inverseroom on 2008-02-10
Hey, you know what?  I think I may have solved it, just by messing with the fonts in Preferences > Content.  Bizarrely the main change I made is changing the proportional font to Serif, the Serif font to Times Roman, the Sans-Serif to Tahoma, and the monospace to Courier New.  I have no idea why this should have worked, but it seems to have done so.

I'll wait a day to see if the problem recurs, and if it doesn't, I'll mark it SOLVED.

Thanks for all your help!

---

### Post by badmedic on 2008-02-10
Glad to hear it... Hope that solves the problem!

---

### Post by inverseroom on 2008-02-10
Actually, I spoke too soon.  Once I started a new session, the formatting problem was back.  Problem unsolved.

---

### Post by inverseroom on 2008-02-16
Final update...whatever the problem was, I fixed it at last by installing FF 3 beta 3.  Yay!

---

### Post by tibellus on 2008-02-23
That's good to hear. It seems that everything was related to Gecko. I think Firefox 3 beta 3 uses Webkit now, that's why your pages look fine.:guitar:

---

### Post by sirwitti on 2008-04-18
hello!
i´m not quite sure, but i had/have the same problem on FF 2 and on several sites.
some text just doesn´t show up until i mark it with the mouse.
but right now i ran into creating a website with joomla 1.5 and the same happened to my navigation.
i messed around a bit and found  out, that this only happened when i used 
```
html { margin-bottom: 1px; }
```
after commenting this out everythings fine.
perhaps this is the same bug as the one you found.
have fun, witti

---

