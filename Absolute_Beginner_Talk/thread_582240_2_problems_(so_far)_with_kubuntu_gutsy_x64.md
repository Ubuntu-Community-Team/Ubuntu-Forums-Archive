---
title: "2 problems (so far) with kubuntu gutsy x64"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by InsertNameHere on 2007-10-19
OK I know it's a new release therefore I understand that problems are unavoidable. 

First off..
What in the world is this
[http://i24.tinypic.com/smblvs.png](http://i24.tinypic.com/smblvs.png)

Now secondly...
When I power off the shutdown bar (like the startup bar, except going backwards) does not appear, It does not appear in the live CD and it does not appear in the installed format.

I will try to install compiz fusion,,,,,
I **HOPE** nothing goes wrong
*crosses fingers*

Thanks for your time.

---

### Post by Anessen on 2007-10-19
That is quite strange. Are all the menus like that? Could be installation media problem, but that's unlikely.

Also, that's a big image, it deforms the forum layout. Please link it instead. :)

---

### Post by InsertNameHere on 2007-10-19
I will fix the image and

it wasn't like that in the install CD as for the first problem

---

### Post by Anessen on 2007-10-19
Just out of curiosity, what language did you set it to?

---

### Post by InsertNameHere on 2007-10-19
Everything english.

---

### Post by Anessen on 2007-10-19
I really don't know. Short of trying to reinstall KDE or Kubuntu as a whole, I don't know what you could try.

Though, I did find this bug report from an old testing version of Gutsy.
[https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/135084](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/135084)

The interesting bit is this:
> 


I you right click the Kmenu then choose Panel Menu->Configure Panel->Menus

You'll see four radio box options that let you choose which
combination and order to show the program name and description in the
menu:
1. Name only
2. Name-description
3. Description only
4. Description (Name)

As far as I'm aware this bug only ever affacted the Name-Description
and Description (name) options, but given that one of those is the
default it affected quite a few people.

If I switched to either Name only or Description only options it
always worked fine for me. I suspect it would be the same for you. I
was just commenting that I no longer seem to have the problem as I can
now choose Name-description and have it work.


---

### Post by InsertNameHere on 2007-10-19
And another problem, there is sound coming out but it's very faint. Everything (settings) is on very top.

Again the menus worked in the LiveCD.

---

### Post by InsertNameHere on 2007-10-19
That solved one problem
Thanks
2 more to go..

---

### Post by wacb on 2007-10-20
Yeah, changing it names or descriptions only works... I had the same problem, this is my first time using linux, is there a way to display names AND descriptions properly?

---

