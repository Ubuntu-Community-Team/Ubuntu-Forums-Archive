---
title: "[SOLVED] Issues with Firefox and Thunderbird (oh my!)"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Kymus on 2007-10-25
**Thunderbird** first

I am aware that by default Thunderbird now disables the automatic display of remote images in an e-mail. I have looked around and what I have read says that there's supposed to be a button you can push when you open an e-mail to display the images (I remember this from windows) and that you can also go into Tools>Options.

Problem: **I got neither.**

I've done my best to comb through all the preferences and options and I'm not seeing anything to change this.... what am I missing??

Now **Firefox**

the spell check is working fine enough, but when I right click a word that is labeled as misspelled, I'm not getting a list of option... I'm just seeing everything *but* word suggestions. 

Uhm.. does this somehow work magically different than it does on windoze? Or am I just lucky?

---

### Post by undadecor on 2007-10-25
Not sure about the Firefox problem, but as far as Thunderbird goes, try going to "Edit", then "Preferences", and then in the window that pops up go to "Privacy" and then the "General" tab.  The options for loading remote images are there.

---

### Post by Kymus on 2007-10-25
> **undadecor said:**
> Not sure about the Firefox problem, but as far as Thunderbird goes, try going to "Edit", then "Preferences", and then in the window that pops up go to "Privacy" and then the "General" tab.  The options for loading remote images are there.

I don't have a "general" tab :-\
[CENTER]
[IMG]http://img229.imageshack.us/img229/5712/thunderbirdbq1.jpg[/IMG]
[/CENTER]

---

### Post by philinux on 2007-10-25
Remember google is a friend "thunderbird remote image"

[http://kb.mozillazine.org/Privacy_basics_(Thunderbird](http://kb.mozillazine.org/Privacy_basics_(Thunderbird))

---

### Post by Kymus on 2007-10-25
> **philinux said:**
> Remember google is a friend "thunderbird remote image"

[http://kb.mozillazine.org/Privacy_basics_(Thunderbird](http://kb.mozillazine.org/Privacy_basics_(Thunderbird))

my search (see above) found me everything *but* that, thanks

Now I can't figure out how to enter about:config in thunderbird :confused:

---

### Post by undadecor on 2007-10-25
"In Thunderbird 1.5 or later, about:config is accessed via "Tools -> Options -> Advanced -> General -> Config Editor (button)". For earlier Thunderbird versions, use the AboutConfig extension."

---

### Post by sailor2001 on 2007-10-25
> **philinux said:**
> Remember google is a friend "thunderbird remote image"

[http://kb.mozillazine.org/Privacy_basics_(Thunderbird](http://kb.mozillazine.org/Privacy_basics_(Thunderbird))

when quoting a url, please check first to see if it is viable......

---

### Post by Kymus on 2007-10-25
> **undadecor said:**
> "In Thunderbird 1.5 or later, about:config is accessed via "Tools -> Options -> Advanced -> General -> Config Editor (button)". For earlier Thunderbird versions, use the AboutConfig extension."

Thanks :)

I read that and was thrown off for a second since my tools menu doesn't have "options" under it. So then I figured I would check preferences and it was there ;).

---

### Post by undadecor on 2007-10-25
Thanks philinux, I had forgotten about that update.

---

### Post by Kymus on 2007-10-25
With my (odd) firefox issue, perhaps the easy solution is a reinstall?

---

### Post by philinux on 2007-10-25
> **sailor2001 said:**
> when quoting a url, please check first to see if it is viable......

How the hell do you think I got it!

---

### Post by philinux on 2007-10-25
> **Kymus said:**
> With my (odd) firefox issue, perhaps the easy solution is a reinstall?

Just go to synaptic and mark firefox for reinstallation.

But first get a terminal up and type firefox -safe-mode and try your spell checker. If you search for firefox safe mode all will be revealed

---

### Post by Kymus on 2007-10-25
Oooh boy, now I'm *really* stumped...

Alright, I edited the about:config so that *mailnews.message_display.disable_remote_image* was toggled to **false**. Closed the preferences menus, tried loading a e-mail that contained images, and nothing. Okay, so then I close Thunderbird and re-open it and still, nothing. Double checked about:config, and it's still toggled like it's supposed to be toggled. 

Still no images.

---

### Post by philinux on 2007-10-25
Mind you personally I would not choose have images displayed by default for the reasons given in the privacy document.

---

### Post by sailor2001 on 2007-10-25
not on my machine

---

### Post by philinux on 2007-10-25
It needs a ) at the end of the url for some reason the message pane cropped it off. :confused:

---

### Post by Kymus on 2007-10-25
> **philinux said:**
> Mind you personally I would not choose have images displayed by default for the reasons given in the privacy document.

I get numerous e-mails throughout the day; most of these are newsletters that depend on the use of images. So unfortunately, this is a necessity.

---

### Post by Kymus on 2007-10-25
> **philinux said:**
> Just go to synaptic and mark firefox for reinstallation.

But first get a terminal up and type firefox -safe-mode and try your spell checker. If you search for firefox safe mode all will be revealed

I used safe mode and it worked just as it should. Reinstalled it through synaptic and it's doing the same thing still :confused: no word suggestions.

---

### Post by jdfreshwater on 2007-10-25
Are you seeing header information? You may want to try the view menu and then to headers and see that you are seeing a normal view.  This may get your image button on the message.  Also have you tried double clicking on a message to open it up in a new window to see the button.

---

### Post by Kymus on 2007-10-25
> **jdfreshwater said:**
> Are you seeing header information? You may want to try the view menu and then to headers and see that you are seeing a normal view.  This may get your image button on the message.  Also have you tried double clicking on a message to open it up in a new window to see the button.

I can see the headers just fine, and even when I open the e-mail by double clicking it, I still don't get anything (image-wise)

---

### Post by philinux on 2007-10-25
> **Kymus said:**
> I used safe mode and it worked just as it should. Reinstalled it through synaptic and it's doing the same thing still :confused: no word suggestions.

If friefox works in safe mode then its one or more of your addons or themes. Disable them one by one, dont forget to restart firefox and you will find the one which is causing the problem.

---

### Post by Kymus on 2007-10-25
> **philinux said:**
> If friefox works in safe mode then its one or more of your addons or themes. Disable them one by one, dont forget to restart firefox and you will find the one which is causing the problem.

it was the [All-In-One Gestures]("https://addons.mozilla.org/en-US/firefox/addon/12"), thanks!

---

### Post by philinux on 2007-10-25
Just got thunderbird to sort then eh!

---

### Post by Kymus on 2007-10-25
> **philinux said:**
> Just got thunderbird to sort then eh!

ha! indeed :)

---

### Post by Kymus on 2007-10-26
ugh, I could use some more help with Thunderbird. Never mind that the images aren't showing up (maybe I should contact Mozilla?), I am now perturbed by two large differences I see that I am not used to based on the windoze version.

When I am composing an e-mail, I noticed that when I maximize the window, the text doesn't even try to fill the screen. That's #1. Now #2 is that I do not see any controls, or keyboard shortcuts  for things like *italics*, **bold**, _underline_, indentation, or linking....

I can't be this screwed.... someone please enlighten me because I must be not understanding something or missing a clear and obvious menu that will allow me to do this (Unless I am to code the html by hand?).

thanks for the help with my daunting questions :P

---

### Post by jdfreshwater on 2007-10-27
For formating go to view -> toolbars -> then click on formating toolbar.  This should bring up the formating for your messages.  As far as your image issue, you can get images if you add the sending address to your address book and click on allow inline images.

---

### Post by jdfreshwater on 2007-10-27
If not seeing image box go to view then Message Body as and choose HTML.  This should allow you to see the box you are looking for.

---

### Post by Kymus on 2007-10-27
> **jdfreshwater said:**
> For formating go to view -> toolbars -> then click on formating toolbar.  This should bring up the formating for your messages.  As far as your image issue, you can get images if you add the sending address to your address book and click on allow inline images.

Seeing the images now, thanks!

However, I'm *not* seeing a formatting toolbar o.O.. just mail and status

---

### Post by philinux on 2007-10-27
You have to click write to compose a new message then view toolbars.

---

### Post by Kymus on 2007-10-27
> **philinux said:**
> You have to click write to compose a new message then view toolbars.

yea.. that's what I did :-\

I think I found an answer [here]("http://www.csc.ncsu.edu/resources/imap_faqs.php") though. Reading it now to see if that answers my final problem with this issue.

---

### Post by Kymus on 2007-10-27
Yup, [that site]("http://www.csc.ncsu.edu/resources/imap_faqs.php") helped :D

> #  The option to turn ON the formatting toolbar will not appear if the HTML emails feature is turned OFF. If you don't see that toolbar then follow these steps:
# Go to the Tools menu and choose the Account Settings command
# Under "Composition and Addressing" turn on "Compose messages in HTML format".
# Next time you click Write, the toolbar option should appear.

Thanks everyone for your help. I believe all of my firefox and thunderbird issues have now been resolved :):)

---

