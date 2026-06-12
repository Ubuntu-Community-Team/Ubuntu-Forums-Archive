---
title: "[SOLVED] Send Link not working Firefox / Thunderbird"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by reset3x on 2007-07-17
Send Link isn't working with Firefox and Thunderbird in Xubuntu 7.04. When I right-click on a web page and chose Send Link nothing happens. Both Firefox and Thunderbird are set as default apps... :-k

Anyone know a fix?

---

### Post by reset3x on 2007-07-18
SOLVED:

In Firefox's Location (URL) Bar, enter:

```
about:config
```

Then press <enter> or click "Go".

With the cursor in the body of the resulting page, <right-click> the mouse.

From the pop-up menu, select "New".

From the next pop-up menu, select "String".

In the pop-up dialog box "Enter preference name", enter:

```
network.protocol-handler.app.mailto
```

Then click "OK".

In the pop-up dialog box "? network.protocol-handler.app.mailto", enter:

```
/usr/bin/mozilla-thunderbird
```

Then click "OK".

---

### Post by NJC on 2007-07-30
Thanks! This worked - although it started out Tbird 1.5.x instead of 2.0 but I guess that could be configured too.

I am still having troubles sending links from other apps though (OpenOffice).

---

### Post by Yako on 2007-12-25
Thanks, worked for me too, although I had to use ```
/usr/bin/thunderbird
```

---

### Post by NJC on 2007-12-27
In Gutsy Send To works perfectly with Thunderbird. It's fantastic ... about time, but a great asset and something I use constantly. 

Merry Christmas to all!

---

### Post by davebgimp on 2008-01-21
I've been wishing "Send Link" would work for the longest time. Thanks.

---

### Post by philinux on 2008-01-21
Works in gutsy and firefox 2 fine. The config in firefox 2 has different preference name.

I Think it's network.protocol-handler.external.mailto the default is true

---

### Post by claprade on 2008-02-21
Great! it worked for me also....Re: network.protocol-handler.external.mailto the default is true
:guitar:

---

### Post by vegaspat on 2008-03-02
I have had this problem for over a week and have tried every suggestion I could find on any board. 

I was hoping the ones here would do the trick since I hadn't seen the option before to change the string on any line.

I've just about run out of ideas and STILL can't use the File/Send link option.  I continue to get an error message with a Windows Internet Explorer Title Bar stating that -Could not perform this operation because the default mail client is not properly installed.

As far as I can tell, Thunderbird works just fine as does Firefox.

Any other ideas that might help?

Thanks.

---

