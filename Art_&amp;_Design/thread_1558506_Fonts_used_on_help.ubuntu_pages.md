---
title: "Fonts used on help.ubuntu pages"
date: 2010-08-22
forum: Art &amp; Design
---

### Post by L_V on 2010-08-22
Something really strange. The fonts used by help.ubuntu.com are:

body {
font-family:"Helvetica Neue","Lucida Grande",Helvetica,Arial,Verdana,sans-serif;
}

Is there any good reason to use microsoft fonts only on ubuntu sites ?

---

### Post by L_V on 2010-08-23
Really no idea why microsoft fonts are used at ubuntu.com ?

Is it intended, or a mistake (frontpage used to make the site for example ?)

Is there any ubuntu package to install these proprietary fonts ?

Your ideas welcome.

---

### Post by kostkon on 2010-08-23
You can find Lucida Grande in [this mac fonts collection]("http://www.ubuntu-unleashed.com/2008/05/howto-install-mac-fonts-on-ubuntu.html").

---

### Post by L_V on 2010-08-23
wget [http://ubuntu-debs.googlecode.com/files/macfonts.tar.gz](http://ubuntu-debs.googlecode.com/files/macfonts.tar.gz)
--2010-08-23 20:15:54--  [http://ubuntu-debs.googlecode.com/files/macfonts.tar.gz](http://ubuntu-debs.googlecode.com/files/macfonts.tar.gz)
Resolving ubuntu-debs.googlecode.com... 74.125.39.82
Connecting to ubuntu-debs.googlecode.com|74.125.39.82|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
2010-08-23 20:15:55 ERROR 403: Forbidden.

But the question I would like to clarify is:
=> why not simply using free fonts on ubuntu.com, fonts simply available in ubuntu repositories ?

---

### Post by jrothwell97 on 2010-08-23
It's not like that.

Firstly, if the MS/Apple fonts aren't available, the system will simply select its default sans-serif font (usually Sans) and display using that.

Additionally, Helvetica, Arial, Verdana and Lucida Grande are all very common fonts, which qualifies them as "web-safe". This means that there's a good bet at least one of those fonts will be on the system, and if not there'll almost definitely be a relatively good match that the system can choose.

So, in short, it's not an issue.

---

### Post by L_V on 2010-08-23
> **jrothwell97 said:**
> Additionally, Helvetica, Arial, Verdana and Lucida Grande are all very common fonts.Sorry but "Lucida Grande" and "Helvetica Neue" are not available on ubuntu system and not so easily found as you say.
I really doubt that the guy in charge of ubuntu.com is using ubuntu system, but most probably vista or windows 7.
Really strange.

---

### Post by jrothwell97 on 2010-08-23
> **L_V said:**
> Sorry but "Lucida Grande" and "Helvetica Neue" are not available on ubuntu system and not so easily found as you say.
I really doubt that the guy in charge of ubuntu.com is using ubuntu system, but most probably vista or windows 7.
Really strange.

Again, it's not relevant. (And if it is anything, it would certainly be Mac OS X, because neither Helvetica Nueue or Lucida Grande are bundled with Windows.)

I, on any of my systems, can manually add "Helvetica Nueue" or "Lucida Grande" to the CSS file. This might well be what happened in this case, probably because this is the font the designer or webmaster deems it to look best in. Alternately (and, I think, most plausibly,) the design might be derived from a pre-made theme which uses these font choices by default.

Even if "the guy in charge of ubuntu.com" (in reality, the team responsible for the themeing of the help.ubuntu.com subsite) did use Windows/Mac OS X, what's the big deal? There is absolutely no reason to force people to use Ubuntu internally, if other software does the job better.

tl;dr: not strange at all.

---

### Post by L_V on 2010-08-24
If you are or have been working for MS/Apple/Google, I understand your point of view.
However, for free/open-source software, requesting or suggesting ubuntu users to steal proprietary fonts is a mistake.
This is very likely why access to these fonts has been forbidden.

---

### Post by mcduck on 2010-08-25
> **L_V said:**
> If you are or have been working for MS/Apple/Google, I understand your point of view.
However, for free/open-source software, requesting or suggesting ubuntu users to steal proprietary fonts is a mistake.
This is very likely why access to these fonts has been forbidden.

There is nothing requiring you to install any fonts. 

The font definitions on CSS are always just *suggestions*, asking your browser that if it has a certain font available and if the user has allowed the browser to sue different fonts on web pages, it should use that font. If it's not available, or the user doesn't allow custom fonts, then the browser tries with the next one on the list. The last option is usually  font family, which is really the only thing you can reasonably well trust the browser to use.

So, when the CSS code lists "Helvetica Neue","Lucida Grande",Helvetica,Arial,Verdana,sans-serif", it sure isn't requiring you to have all, or even any of those fonts available. Instead it checks if you happen to have Helvetica Neue, and if you do it then uses it. If not, it checks for Lucida Grande, after that Helvetica, and so on until the "sans-serif"-point where it just uses whatever is set as the default sans-serif font in your browser's options.

While it would be nice to see a open-source font on the list, it wouldn't make much of a difference. The page would still have to define fonts commonly available on other platforms as well, and in the end every Ubuntu user is already viewing the page using an open-source font unless they have themselves set a proprietary font as the default in their browser... ;)

---

### Post by Grenage on 2010-08-25
I'd imagine that they want the site to look nice for those who might not yet be using Ubuntu or any Linux, which means that those people are likely Windows users (and will have the fonts).

There's nothing off here, really.

---

### Post by L_V on 2010-08-26
The reason I raised the point is simply that very often, I observe that the font rendering is very bad on some ubuntu sites.
After css analysis, I understand why.
But Ok, there are more than 99% of windows/MAC users, and less than 1% of linux users.
I just wonder if windows users often visit ubuntu.com.
I would bet that no.
I then need to play some ".fonts.conf" file to replace proprietary fonts I don't have by others.
Not sure a new comer to ubuntu will appreciate to start tweaking his system due to the lack of proprietary fonts, to visit sites promoting open-source (or supposed to).
Anyway, I don"t really need ubuntu.com.
Then, just an observation, to not say a strangeness.

---

### Post by warrenc285 on 2010-08-26
> **L_V said:**
> The reason I raised the point is simply that very often, I observe that the font rendering is very bad on some ubuntu sites.
After css analysis, I understand why.
But Ok, there are more than 99% of windows/MAC users, and less than 1% of linux users.
I just wonder if windows users often visit ubuntu.com.
I would bet that no.
I then need to play some ".fonts.conf" file to replace proprietary fonts I don't have by others.
Not sure a new comer to ubuntu will appreciate to start tweaking his system due to the lack of proprietary fonts, to visit sites promoting open-source (or supposed to).
Anyway, I don"t really need ubuntu.com.
Then, just an observation, to not say a strangeness.

Bad font rendering isn't the websites fault, it's the fault of whatever your default font is in your browser. Also, a newcomer wouldn't have to do any of that. As was already explained, if you don't have any of the fonts listed the website will simply use your default font.

---

### Post by mcduck on 2010-08-26
> **L_V said:**
> 
I then need to play some ".fonts.conf" file to replace proprietary fonts I don't have by others.
No, you don't. Just set default fonts you like in your browser's settings, and ubuntu.com will use them. :)

That's what the "sans-serif" at the end of the definition is for, it tells your browser which of your default fonts it should use.

The only sensible open-source font I could even think of adding to that definition would be Bitstream Vera Sans, which happens to be the default font in Ubuntu so adding it to the font definition would make no difference. ;)

If you have problems with font rendering you should probably check your font options in Ubuntu, especially the advanced options. Setting a correct DPI and subpixel order for your monitor makes a huge difference in font rendering quality.

---

### Post by L_V on 2010-08-27
> **mcduck said:**
> No, you don't. Just set default fonts you like in your browser's settings
Disagreed.
I set the defaut fonts for best **system** settings (for menus etc), and not for ubuntu.com forums.

Well, in summary, if proprietary fonts needs to be implemented in css of some ubuntu.com sites for any reason I don't understand, that's not a major issue, but a better clarification would have been appreciated.
Thanks anyway.

---

### Post by Grenage on 2010-08-27
> **L_V said:**
> Well, in summary, if proprietary fonts needs to be implemented in css of some ubuntu.com sites for any reason I don't understand.

They aren't implemented, that's the point; they are listed as a choice, to be used IF the OS has those fonts.

---

### Post by L_V on 2010-08-27
_To make it very clear_:
I think ajusting good font settings in a linux system is hard enough to not make life even harder with "Helvetica Neue, Lucida Grande" fonts you can be sure no ubuntu users will find in ubuntu repositories.
Make it simple, and do not focus on windows/MAC users as a top priority !!!

---

### Post by mcduck on 2010-08-28
> **L_V said:**
> Disagreed.
I set the defaut fonts for best **system** settings (for menus etc), and not for ubuntu.com forums.

Well, in summary, if proprietary fonts needs to be implemented in css of some ubuntu.com sites for any reason I don't understand, that's not a major issue, but a better clarification would have been appreciated.
Thanks anyway.

The browser has it's own font settings, it doesn't use the fonts set in your desktop environment's font options but the font set in the *browser's* options. :D

---

### Post by mcduck on 2010-08-28
> **L_V said:**
> _To make it very clear_:
I think ajusting good font settings in a linux system is hard enough to not make life even harder with "Helvetica Neue, Lucida Grande" fonts you can be sure no ubuntu users will find in ubuntu repositories.
Make it simple, and do not focus on windows/MAC users as a top priority !!!

To make it even more clear:
The site *does not require* you to have any, or all, of the fonts listed. 

It only asks if you *might* have *one* of them, and if not then picks the default sands-serif font, as set in your browser's font options.

---

### Post by lisati on 2010-08-28
Please! I'm getting dizzy watching this thread go round in circles. :D:D

---

### Post by L_V on 2010-08-28
> **mcduck said:**
> It only asks if you *might* have *one* of them, and if not then picks the default sands-serif font, as set in your browser's font options.It does not.
Default sans-serif font is set to Arial on my browser, and Arial is ok for system and browser setting.
And ubuntu.com site is specifically ugly.
Well, if somebody understands why "Helvetica Neue, Lucida Grande" fonts are justified for ubuntu, fine.
But just sounds ridiculous.
Make it simple whenever possible.

---

### Post by Merk42 on 2010-08-28
> **lisati said:**
> Please! I'm getting dizzy watching this thread go round in circles. :D:D
Maybe once the new Ubuntu font gets finalized, Ubuntu.com will provide it in woff, otf, eot and svg formats and use it across the site via @font-face and that will make everyone happy.

---

### Post by mcduck on 2010-08-29
> **L_V said:**
> It does not.
Of course it does. This isn't something you could even argue about. If you feel otherwise, please read about CSS font definitions first. [http://www.w3schools.com/css/css_font.asp]("http://www.w3schools.com/css/css_font.asp"):D

And note that the browser's font settings are in Edit/Preferences, Content-tab, and under Fonts & Colors click the Advanced-button. You'll get a dialog for setting the proportional, serif, sans-serif and monospace fonts for your browser.

The other fonts are justified because they are for other people to use, people who run Windows or OSX and thus have those fonts instead of what Ubuntu has.

---

### Post by L_V on 2010-09-07
> **mcduck said:**
> Of course it does.No. It only does only if you **force** the font settings.
If you use Firefox, you will find this option:

"*Allow pages to choose their own fonts, instead of my selections above.*"

Only ubuntu.com is raising this problem and would force the user to choose this font option, which means, forget the site fonts.
The problem is the exotic font setting of ubuntu.com, nothing else.

---

### Post by mcduck on 2010-09-07
You don't need to force the browser to only use your default fonts, like I have already explained the font definition in CSS suggests several fonts, in order of preference, and if none of them are available then uses your browser's default fonts.

That setting will only disable use of such font selection completely, and always forces the browser to use the default font, even if you have one of the fonts defined in CSS. So you don't need to force your own fonts unless you never, ever want to see any other font used on web pages. The default fonts are _always_ automatically used if any of the fonts suggested in CSS aren't available.

> 
The font family of a text is set with the font-family property.

The font-family property should hold several font names as a "fallback" system. If the browser does not support the first font, it tries the next font.

Start with the font you want, and end with a generic family, to let the browser pick a similar font in the generic family, if no other fonts are available.

[http://www.w3schools.com/css/css_font.asp]("http://www.w3schools.com/css/css_font.asp")
[http://www.w3.org/TR/CSS2/fonts.html]("http://www.w3.org/TR/CSS2/fonts.html")

---

### Post by DoubleClicker on 2010-09-10
> **L_V said:**
> It does not.
Default sans-serif font is set to Arial on my browser, and Arial is ok for system and browser setting.
And ubuntu.com site is specifically ugly.
Well, if somebody understands why "Helvetica Neue, Lucida Grande" fonts are justified for ubuntu, fine.
But just sounds ridiculous.
Make it simple whenever possible.

Everyone is missing the actual "problem" that LV is complaining about. 
it's not that the CSS forces him to have a font that he **doesn't** have,  it's that he **has** one of the listed fonts, and he thinks it looks ugly.  If he didn't have  one of them , then everything  would  display in Arial, which he thinks is OK.    

LV, check your installed fonts, I bet you will find one the ones listed in the CSS is installed on your system.

---

### Post by @B6Mwu8fN9M on 2010-09-11
Let me try to clarify:

Ubuntu.com is used to advertise Ubuntu. They're trying to convert Windows users; so they list Windows fonts. They're trying to convert Mac users; so they list Mac fonts.

For Ubuntu, they put the 'sans-serif' at the end. It's known what the default is for Ubuntu so there's not need to specify it. And that list is common in sites' CSS (if they specify fonts). 

Arial is a VERY common font. Windows users have it. (not sure about Mac; maybe with Word install.). The metrics for the font are clear and Free fonts exist with the same metrics to replace it; I haven't really noticed the difference before and after installing the mscorefonts package. 

Again, they're VERY common fonts. Even W3C lists them when talking about CSS fonts. And look at that! You've got it installed as well.

So I don't see the problem. Saying either Arial or specifying the Free alternative will have almost no difference in the look of the site. Once they finish working on their own fonts, that's probably when they'll change stuff, but they'll probably leave the Arial in there just in case there's a browser without @font-face support.

---

### Post by L_V on 2010-10-09
As even Helvetica font is a strange animal not available in any ubuntu package (even not a MS font), to solve it, I have added this in ~/.fonts.conf

```
<match target="pattern">
 <test qual="any" name="family" compare="eq">
  <string>Helvetica</string>
 </test>
 <edit name="family" mode="prepend" binding="same">
  <string>Arial</string>
 </edit>
</match>
```

and now, help.ubuntu.com looks fine.

---

