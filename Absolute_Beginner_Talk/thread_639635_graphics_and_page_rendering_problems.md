---
title: "graphics and page rendering problems"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2007-12-13
OK, I don't really know what "page rendering" means, I am just trying to sound less like an idiot and failing.

Anyway, the problems  I have might be all interelated so I will mention them all. 

First off,  I cannot enable desktop effects, even after enabling restricted drivers. A time or two I have been able to briefly get them to work after following instructions I find searching other threads but never for long.

Second, certain pages, especially in Firefox don't show up correctly. Specifically I am posting a screenshot of a page that I use for work where text from one button runs down into the next button so that you can't read either word. I use that page everyday so I know what button to push but you can see how that might be a problem. 

The last issue I have is that Firefox seems to constantly want to hang and crash. I have never had that problem with Firefox before and it only happens on this computer out of all of the three that I have installed 7.10 on.

These all seem graphics related but I don't know. Any help would be very appreciated.

---

### Post by boriquajake on 2007-12-13
I must be doing something wrong with the way I post questions here. It seems like the last several times I have tried to get help I have not had any responses. I have read the guidlines and I have tried searching before posting. I have tried to give specifics about the problem. I wonder if my specific issues are ones that have been asked and answered so many times that people are sick of them. Is it that I am just no good at searching and recognizing related threads? Am I wording things in a way that is somehow "anti-linux"?

---

### Post by Samhain13 on 2007-12-13
> Second, certain pages, especially in Firefox don't show up correctly. Specifically I am posting a screenshot of a page that I use for work where text from one button runs down into the next button so that you can't read either word. I use that page everyday so I know what button to push but you can see how that might be a problem.

This maybe an unrelated problem. It could be that the site wasn't designed for Firefox? I wasn't able to go to the page you posted in your screenshot because I do not have an account so I cannot test it in my other browsers.

A quick remedy for you to try is to reduce the text size when viewing this page. View > Text Size > Decrease, or simply Control+Minus Key.

---

### Post by boriquajake on 2007-12-13
> **Samhain13 said:**
> This maybe an unrelated problem. It could be that the site wasn't designed for Firefox? I wasn't able to go to the page you posted in your screenshot because I do not have an account so I cannot test it in my other browsers.

A quick remedy for you to try is to reduce the text size when viewing this page. View > Text Size > Decrease, or simply Control+Minus Button.


Thanks for the tip. I will definitely try that.

The weird thing is that it doesn't occur on the other computer that I run Ubuntu on. Would screen size and make a difference or does that mean that it is not the website but my computer?

---

### Post by boriquajake on 2007-12-13
> **Samhain13 said:**
> This maybe an unrelated problem. It could be that the site wasn't designed for Firefox? I wasn't able to go to the page you posted in your screenshot because I do not have an account so I cannot test it in my other browsers.

A quick remedy for you to try is to reduce the text size when viewing this page. View > Text Size > Decrease, or simply Control+Minus Key.

Wow, that did the trick for that problem. Thank you very much! The simplest things can throw me off.

---

### Post by Samhain13 on 2007-12-13
Do you have the same Appearance Preferences set for both computers?

If the remedy I mentioned works, then perhaps on that computer, the default font size for your desktop applications is too big. That's why you need to reduce the font size to properly view that page.

I don't think screen size should have anything to do with the problem, whatever the case may be. :)

[edit]
Oh! We must have posted at the same time. I'm glad that helped.

---

### Post by boriquajake on 2007-12-13
> **Samhain13 said:**
> Do you have the same Appearance Preferences set for both computers?

If the remedy I mentioned works, then perhaps on that computer, the default font size for your desktop applications is too big. That's why you need to reduce the font size to properly view that page.

I don't think screen size should have anything to do with the problem, whatever the case may be. :)

[edit]
Oh! We must have posted at the same time. I'm glad that helped.

Thanks again for the help with that problem. Do you have any suggestions on the other issues with desktop effects and firefox hanging?

---

### Post by philinux on 2007-12-13
Firefox,

Type ```
about:config 
``` in the address bar press enter.

In filter type ipv6

double click the entry to change the boolean to true.

See if that helps

Also from terminal type firefox -safe-mode 

run it see if its better if so one or more of your addons may be the cause

---

### Post by boriquajake on 2007-12-13
> **philinux said:**
> Firefox,

Type ```
about:config 
``` in the address bar press enter.

In filter type ipv6

double click the entry to change the boolean to true.

See if that helps

Also from terminal type firefox -safe-mode 

run it see if its better if so one or more of your addons may be the cause

Thank you for responding,  I get the feeling that what you are saying is going to help me, but I am confused.. I opened terminal and pasted what you said but it told me that the command was not found. I just assumed that you meant terminal because in the past whenever someone has told me to "code" that is what they meant. Sorry for being obtuse.

---

### Post by Samhain13 on 2007-12-13
> Thanks again for the help with that problem. Do you have any suggestions on the other issues with desktop effects and firefox hanging?

You're welcome. I have no suggestions for the remaining issues though, sorry.

Hummm... as to Philinux's command:
```
firefox -safe-mode
```
it worked fine on my end. Maybe you forgot to put a space between "firefox" and "-safe-mode"?

---

### Post by boriquajake on 2007-12-13
> **Samhain13 said:**
> You're welcome. I have no suggestions for the remaining issues though, sorry.

Hummm... as to Philinux's command:
```
firefox -safe-mode
```
it worked fine on my end. Maybe you forgot to put a space between "firefox" and "-safe-mode"?

I hadn't even gotten to the point of trying the part about firefox. 

Anyway I just did what you said and it opened up a new window. Does this mean that from now on when I open firefox it will be in safe mode?

---

### Post by philinux on 2007-12-13
It's just a one off is safe mode for debugging.

```
about:config
```  goes in the address bar of firefox.

---

### Post by Samhain13 on 2007-12-13
> I hadn't even gotten to the point of trying the part about firefox.

Oops! Sorry. Anyway, I'll leave you with philinux now as it seems he can be of more help to you regarding this issue.

Good luck. :)

---

### Post by boriquajake on 2007-12-13
> **Samhain13 said:**
> Oops! Sorry. Anyway, I'll leave you with philinux now as it seems he can be of more help to you regarding this issue.

Good luck. :)

Got it. Between you and the other gentleman I might have the Firefox issue solved. It is hard to tell because the problem is intermittent, but thanks for the help so far.

Do you have any suggestions as to how I can get desktop effects to enable?

---

### Post by philinux on 2007-12-13
Quick tip to get problems solved. Dont mix up more than one problem in a post. Keep each separate and to the point.

Post a new thread about getting Desktop effects working and always try to post your pc specs for a techy query.

---

### Post by boriquajake on 2007-12-13
> **philinux said:**
> Quick tip to get problems solved. Dont mix up more than one problem in a post. Keep each separate and to the point.

Post a new thread about getting Desktop effects working and always try to post your pc specs for a techy query.

That is very good advice. I will be sure to follow it in the future. What specs would be the most relevant to post? Is a make and model sufficient or should I do something more?

---

### Post by philinux on 2007-12-13
Plus

Processor
Memory
Graphics card 

Would be good.

---

### Post by boriquajake on 2007-12-13
> **philinux said:**
> Plus

Processor
Memory
Graphics card 

Would be good.


OK, here is my last stupid question for this topic. Where do I get the specifics on those things? I seem to remember someone showing me a terminal command something like
"lsci" or something but I can't remember now.

---

