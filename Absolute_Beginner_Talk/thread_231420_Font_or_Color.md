---
title: "Font or Color?"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by bladefallcon on 2006-08-07
Ok...I have a feeling it has something to do with colors...but im not sure, so ill ask. A few websites I frequent the biggest being [www.wwe.com](www.wwe.com) (yes yes..i watch wrestling, and enjoy it..so sue me) as it is, I have already found a few problems with sites like this IE: all of the streaming video on the site requires Windows Media Player, which sucks...but Im not so much worried about that. My question is this: All of the headlines on the site, are just white blocks of space. At first, I thought maybe a font issue. They work fine on windows based systems, but not on my linux systems. Then I realised something. If i highlight that area, the text is there, I can read it. Which leads me to believe it is not a problem with the font, but perhaps the colors used? Its not the browser...i use firefox on all systems..wether be linux or windows. So I must believe that the problem, wether be fonts or colors, is linux itself. Anyone else come across this problem? Can it be fixed?

---

### Post by editrix on 2006-08-07
> **bladefallcon said:**
> ...If i highlight that area, the text is there, I can read it. Which leads me to believe it is not a problem with the font, but perhaps the colors used? Its not the browser...i use firefox on all systems..wether be linux or windows. So I must believe that the problem, wether be fonts or colors, is linux itself. Anyone else come across this problem? Can it be fixed?

I had a very similar problem with my Hoary install (now using Dapper). I couldn't see any of the code in the HowTo pages here, or on some other sites. But I could run my mouse over the area, and paste the text into an editor. I posted about it and never got an answer, although people tried. No one suggested it might be a colour problem, but when I used Opera in ... (sorry, forget the term, but NOT author mode--i.e., all the text was black) I could read it. So it might very well be a colour problem.

Installing Opera just to find out is a PITA. What browser(s) are you using?

---

### Post by bladefallcon on 2006-08-07
> **editrix said:**
> I had a very similar problem with my Hoary install (now using Dapper). I couldn't see any of the code in the HowTo pages here, or on some other sites. But I could run my mouse over the area, and paste the text into an editor. I posted about it and never got an answer, although people tried. No one suggested it might be a colour problem, but when I used Opera in ... (sorry, forget the term, but NOT author mode--i.e., all the text was black) I could read it. So it might very well be a colour problem.

Installing Opera just to find out is a PITA. What browser(s) are you using?

I am using firefox, both on my windows system, and my linux systems..But the problem only happens in Linux..I kinda get the feeling, that perhaps, the color, of the text/background color where those texts are is maybe just not supported (or mayber i need to download a package for them?) Because the text is definantly there..i just cant see it, until i highlight it...It isnt the browser..its linux..

---

### Post by greybirds on 2006-08-07
I couldn't get what you describe to happen on the wwe site until I enabled javascript (I have the noscript extension installed with scripting turned off globally by default). 

No javascript: page looks fine.

Javascript: blocks of previously visible text are replaced with blocks of white on white text in a different font.

I dug around a bit in wwe.com's code and they're doing some pretty funky things. My guess is that their code isn't standards compliant and they haven't bothered checking it against anything but a windows machine. 

Just out of curiousity, turn off javascript and try loading the page. See if you have the same problem then. (To turn off javascript in Linux's version of Firefox: Edit -> Preferences, click the Content tab, and uncheck "Enable Javascript"). If it works without js, then it will narrow what we need to check considerably.

---

### Post by bladefallcon on 2006-08-07
> **greybirds said:**
> I couldn't get what you describe to happen on the wwe site until I enabled javascript (I have the noscript extension installed with scripting turned off globally by default). 

No javascript: page looks fine.

Javascript: blocks of previously visible text are replaced with blocks of white on white text in a different font.

I dug around a bit in wwe.com's code and they're doing some pretty funky things. My guess is that their code isn't standards compliant and they haven't bothered checking it against anything but a windows machine. 

Just out of curiousity, turn off javascript and try loading the page. See if you have the same problem then. (To turn off javascript in Linux's version of Firefox: Edit -> Preferences, click the Content tab, and uncheck "Enable Javascript"). If it works without js, then it will narrow what we need to check considerably.

Ok...i hadnt thought of the java script...im dissappointed in myself for not thinkong of that..And your right...they are doing some funky stuff in their code..(being a web page designer myself, I had looked through the coding as well...still kicking myself for not thinking of javascript.)

Only one problem..The main part of the page (with the pictures, that are supposed to change on a regular time interval) no longer functions...so any of the news articles they have there are now none viewable..One way or another, I am now convinsed this is has nothign to do with anything other than them not being conciderate of Linux users..

Ill probably email them again, and see what i can do about that...not much most likely...but at least they will hopefully start to get the hint..

Edit:

Any even worse problem...With javascript turned off, while i can now read the headlines on that page, Gmail no longer loads (unless i go with the non-javascript version)

---

### Post by greybirds on 2006-08-07
I dug around some more into their code. They're using the sIFR flash file to render the text in question and inserting it with an embed tag generated with javascript. That's why it works when javascript is turned off - you're just getting regular HTML.

When you turn javascript on, it inserts those flash files which render the text in the font they want, in white text. The flash plugin for linux firefox has issues; one being that it draws a white box under itself in some cases and refuses to stop. That seems to be the problem here - white text on a white background. There are workarounds for it and I'd've hoped the people wwe hired to write their site new about them, but apparently not.

In short, it's an issue with Adobe/Macromedia's crappy plugin and wwe's ignorance of how to work with it. I'm not sure what to tell you; it seems to be a matter of what you want to see on the site, unless you can convince them (and the other sites) to fix their code.

Here's an example of sIFR being used correctly, if you're interested:
[http://www.mikeindustries.com/blog/files/sifr/2.0/]("http://www.mikeindustries.com/blog/files/sifr/2.0/")

Oh, and turn javascript back on and seriously think about getting the NoScript extension for Firefox. It'll let you turn scripting on and off for individual sites. It helps ensure your privacy and it helps speed things up.

---

### Post by MJSOnline on 2006-09-20
With regards to the wwe.com site, How do you play the videos on the site?  What plugins do I need?  M

---

