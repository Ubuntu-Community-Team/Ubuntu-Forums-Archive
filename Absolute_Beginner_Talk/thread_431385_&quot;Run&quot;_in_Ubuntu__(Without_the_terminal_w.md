---
title: "&quot;Run&quot; in Ubuntu?  (Without the terminal window open indefinately)"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by willz06jw on 2007-05-03
Howdy,

I am trying to find an option that is just like "Run" in Windows.  I don't want to type it in the terminal window, because if I do that the program shuts down if I close the terminal window.

Thanks,
Will from Texas

---

### Post by 5-HT on 2007-05-03
Alt + F2 brings up a 'Run Application' window.

---

### Post by willz06jw on 2007-05-03
Thanks, that worked perfectly.

I wonder why Run isn't under the accessories menu?

Thanks again,
Will from Texas

---

### Post by zvacet on 2007-05-03
You can run app just typing the name in terminal.

---

### Post by igknighted on 2007-05-03
> **zvacet said:**
> You can run app just typing the name in terminal.

He knows that, the problem is then you must leave that terminal window open.

@ the OP: I think it is in one of the menus, maybe system or places?

---

### Post by teddybairs1 on 2007-05-03
You can add an applet to one of the taskbars, either above or below, for running a command. Just right click on the taskbar and then select "Add to Panel". The applet for running a command should be somewhere in the list. In Kubuntu you just right click on the desktop and select "run command."

---

### Post by aysiu on 2007-05-03
> **igknighted said:**
> He knows that, the problem is then you must leave that terminal window open. Not if you use [i]&[/i/]

For example: ```
firefox
``` leaves the terminal window open. If you close the terminal, Firefox, too, will close.

```
firefox &
``` however, let's you close the terminal window and keep Firefox open.

---

### Post by mcduck on 2007-05-03
> **aysiu said:**
> Not if you use [i]&[/i/]

For example: ```
firefox
``` leaves the terminal window open. If you close the terminal, Firefox, too, will close.

```
firefox &
``` however, let's you close the terminal window and keep Firefox open.
I don't think that works. Adding the '&' only starts Firefox in background, leaving the terminal usable for other tasks. But closing the terminal will still also close Firefox.

The working solution is to use 'nohup'. So, in case of Firefox, the command would be 'nohup firefox &'. Now you can close the terminal, and Firefox will stay open.

---

### Post by aysiu on 2007-05-03
> **mcduck said:**
> I don't think that works. Adding the '&' only starts Firefox in background, leaving the terminal usable for other tasks. But closing the terminal will still also close Firefox. Works fine for me--I just tried it. There's no reason closing the terminal on ```
firefox &
``` should also close Firefox; that's what running the background means.

---

### Post by mcduck on 2007-05-03
> **aysiu said:**
> Works fine for me--I just tried it. There's no reason closing the terminal on ```
firefox &
``` should also close Firefox; that's what running the background means.

That's strange, as it doesn't work for me. I need the 'nohup' or all programs opened from a terminal will close with the terminal :confused:

---

### Post by aysiu on 2007-05-03
I wonder if I have some kind of weird special configuration... or if you do.

Anyone else? What has been your experience with using *&* and closing the terminal afterwards?

---

### Post by Delkster on 2007-05-03
> **willz06jw said:**
> I wonder why Run isn't under the accessories menu?
It used to be in the menus in some older releases but it was removed at some point, probably in the name of simplicity.

---

### Post by ahmatti on 2007-05-03
> **mcduck said:**
> That's strange, as it doesn't work for me. I need the 'nohup' or all programs opened from a terminal will close with the terminal :confused:

I just also tried and I noticed that firefox& doesn't need 'nohup' to stay open after you close the terminal, but some others like e.g acroread& do...

---

### Post by STREETURCHINE on 2007-05-03
> **aysiu said:**
> I wonder if I have some kind of weird special configuration... or if you do.

Anyone else? What has been your experience with using *&* and closing the terminal afterwards?

nope works for me 


               ```
firefox &
```

---

### Post by mcduck on 2007-05-03
> **aysiu said:**
> I wonder if I have some kind of weird special configuration... or if you do.

Anyone else? What has been your experience with using *&* and closing the terminal afterwards?

As far as I know, I have no special configuration. Every program I tried closes with the terminal if I don't use 'nohup'.

---

### Post by tanelt on 2007-05-03
> **aysiu said:**
> Anyone else? What has been your experience with using *&* and closing the terminal afterwards?


I'm using a fresh install of Ubuntu (just intstalled a few days ago) and here's my experience:

```
firefox &
```

... starts Firefox, but closing the terminal **also** closes Firefox. However, if firefox is **already running** and this command is used, closing the terminal doesn't seem to close any Firefox windows.

```
nohup firefox &
```

... starts Firefox and closing the terminal doesn't close Firefox, but this leaves the terminal unusable unless I press CTRL+C or the Enter key.

---

### Post by Rui Pais on 2007-05-03
> **aysiu said:**
> I wonder if I have some kind of weird special configuration... or if you do.

Anyone else? What has been your experience with using *&* and closing the terminal afterwards?

well, as far as i know the '&' detach the command for the one who call it (the parent), that in that case would be the  shell line command, not the all Terminal window. Some times, some applications with a DE/WM survive the closing of the terminal, some times they close. Changing one of the parameters, either the app, the terminal or the de/wm, may close it. 

I don't no why some survive. In my case now, either swiftfox & and firefox & close with the closing of the terminal. But in the past i experienced the opposite with the exception of xterm that always closed any app i run from it with &...

My suggestion is never count on the '&' for sure, special if you are running some app where you are working with your data (text, code, images). One can easily loose it.

---

