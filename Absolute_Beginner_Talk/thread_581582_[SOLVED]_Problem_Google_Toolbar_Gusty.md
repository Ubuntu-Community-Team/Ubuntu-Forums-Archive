---
title: "[SOLVED] Problem Google Toolbar Gusty"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by rawr215 on 2007-10-19
Greetings.
I am fairly new to linux and this is my 2nd time trying out Ubuntu.  I actually have the opportunity to install it on my laptop now that I have graduated from college.

As the title of this tread, i am having problem with Google tool bar with the new gusty gibbons.  For some reason, the bookmark button does not work.  It will not load my bookmarks using the google toolbar.  If u click the down arrow, it keep saying "downloading bookmarks..."

I was wondering if anyone else is experiencing this as Gusty just came out yesterday.  

Thanks ahead of time

Jim

---

### Post by slughappy1 on 2007-10-19
I am having the same problem. I had the same problem with the beta, but I didn't have the problem with feisty. Anyone else have any idea why this is happening?

---

### Post by wormser on 2007-10-19
Try uninstalling it and installing it again from [here]("http://www.getfirefoxplus.com/").

---

### Post by rawr215 on 2007-10-19
Still having the same problem even after uninstalling and using the following link to reinstall >_<

---

### Post by ebeckhusen on 2007-10-19
Did you try uninstalling the tool bar and then reinstalling from [toolbar.google.com]("http://toolbar.google.com")?  I was having the same problem as you, and this just worked for me.

---

### Post by rfruth on 2007-10-19
No problem here.

---

### Post by xWHEELSx on 2007-10-19
I am haveing the same troulbe, it worked in 7.4 but not in 7.10. I tried reinstall and sign in again.  I can see all my gmail from toolbar not bookmarks

---

### Post by rawr215 on 2007-10-20
rfruth - how come your's work? XD

---

### Post by rawr215 on 2007-10-20
Learned thing new!
went to error console and found this

Error: Cc['@google.com/toolbar/bookmark-wrapper;1'] has no properties
Source File: file:///home/jimmy/.mozilla/firefox/u9w14kix.default/extensions/%7B3112ca9c-de6d-4884-a869-9855de68056c%7D/lib/toolbar.js
Line: 150

I think i saw someone with a similar error while searching for other post about this problem

---

### Post by locutusoftrek on 2007-10-20
I have the same problem.
I tried to reinstall the toolbar, but the problem remains.
Anyone has a solution?

---

### Post by ebeckhusen on 2007-10-20
Okay, I had had the toolbar working before, but then I reinstalled Ubuntu and it stopped working.  A search on Google brought up these directions, and they worked for me.  You may have to disable the bar, then re-enable it for it to work.
--------------------------------
Close Firefox.
Click on System / Administration / Synaptic Package manager   (The
path may be different for your Kubuntu. I use Ubuntu)
Click on Search
Type in "gcc" without quotes.
look through what comes up and mark to install "gcc-3.3-base
(1:3.3.6-15ubuntu2)", or newer.
Do another Search for glibc-doc (2.6.1-0ubuntu1 ) and mark for
installation
And once more for libstdc++5 (1:3.3.6-15ubuntu2) and mark for
installation.

Apply those so they install.
------------------------------------

---

### Post by jgonzalezo0501 on 2007-10-21
I have the same problem, and i think it was just me, but no there are many users whit the same problem, i can't use my bookmarks!!!
Help please

---

### Post by locutusoftrek on 2007-10-22
I had the problem posted, but with the post above (really, two posts above) and, in fact, the instructions given by Google as requirements for the installation of the toolbar under Linux (see the web page), i solved the problem.

Try going to the toolbar web page

---

### Post by xWHEELSx on 2007-10-22
> **ebeckhusen said:**
> Okay, I had had the toolbar working before, but then I reinstalled Ubuntu and it stopped working.  A search on Google brought up these directions, and they worked for me.  You may have to disable the bar, then re-enable it for it to work.
--------------------------------
Close Firefox.
Click on System / Administration / Synaptic Package manager   (The
path may be different for your Kubuntu. I use Ubuntu)
Click on Search
Type in "gcc" without quotes.
look through what comes up and mark to install "gcc-3.3-base
(1:3.3.6-15ubuntu2)", or newer.
Do another Search for glibc-doc (2.6.1-0ubuntu1 ) and mark for
installation
And once more for libstdc++5 (1:3.3.6-15ubuntu2) and mark for
installation.

Apply those so they install.
------------------------------------

Thank you  Bookmarks are now working fine,   Good directions, Thanks once again
:):):)

---

### Post by rawr215 on 2007-10-22
i have followed the provided instructions carefully and still can not use my book mark button... i never thought linux can be so complicated

Seems like everyone else are doing fine by following the given instructions but me

should i try uninstalling and reinstalling something next?

---

### Post by rawr215 on 2007-10-22
Okay,
I have uninstalled the toolbar and reinstalled it after downloading the things as instructed above
It works now!
I have set the thread post as solved

Thank you everyone for helping me.
I hope installing ubuntu and joinning this linux community was the right move.
So far everyone are helpful and nice!

---

### Post by amilak on 2008-02-14
I've tried above methods but didn't solve the problem. 
But finally this method solve the problem. Now bookmarks are fine.... :)

[http://groups.google.com/group/FFToolbar-group-GettingStarted/browse_thread/thread/1ea24590741e4242/4ed3f985a4e0fab9?lnk=gst&q=#4ed3f985a4e0fab9](http://groups.google.com/group/FFToolbar-group-GettingStarted/browse_thread/thread/1ea24590741e4242/4ed3f985a4e0fab9?lnk=gst&q=#4ed3f985a4e0fab9)

---

### Post by MetalPrincess on 2008-02-16
> **ebeckhusen said:**
> Did you try uninstalling the tool bar and then reinstalling from [toolbar.google.com]("http://toolbar.google.com")?  I was having the same problem as you, and this just worked for me.

Thanks worked for me! :D


MP

---

