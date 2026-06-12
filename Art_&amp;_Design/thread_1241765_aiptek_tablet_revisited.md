---
title: "aiptek tablet revisited"
date: 2009-08-16
forum: Art &amp; Design
---

### Post by mystmaiden on 2009-08-16
I've upgraded to Jaunty and would like to try again to get my aiptek tablet working. The link for directions that was given to me here is:

I'[HTML] https://help.ubuntu.com/community/AiptekTablet[/HTML]

Before I do anything rash, I want to make sure I understand it though (it does make me feel better that I don't have to try and mess with the xorg file now, but still..) The instructions say > Create the file 10-aiptek.fdi, in the directory /etc/hal/fdi/policy with content:  and it lists the content. 
```
<?xml version="1.0" encoding="UTF-8"?> 
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="Aiptek">
      <merge key="input.x11_driver" type="string">aiptek</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true </merge>
      <merge key="input.x11_options.USB" type="string">On</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="input.x11_options.Mode" type="string">absolute</merge>
    </match>
  </device>
</deviceinfo>
```

What I am not clear on is how to create the needed 10-aiptek.fdi. Will just running the aforementioned code create it, or must I create the file somehow and Then run the code? 

Thanks much
myst

---

### Post by Favux on 2009-08-16
Hi mystmaiden,

> or must I create the file somehow
Yes.  In a terminal enter:
```
gksudo gedit /etc/hal/fdi/policy/10-aiptek.fdi
```
Then in the blank file that pops up copy and paste into it the entire contents of the .fdi file you are installing.  Save, close, and reboot.

To refine it you might try entering in a terminal:
```
xinput --list
```
before and after you install the 10-aiptek.fdi and save each output as before and after "whatever you want to call it".

We've been messing around with the .fdi and our current version is on post #50 here:  [http://ubuntuforums.org/showthread.php?t=1191826&page=5](http://ubuntuforums.org/showthread.php?t=1191826&page=5)  Some of the parameters in the .fdi may change depending on which aiptek tablet you have.

---

### Post by mystmaiden on 2009-08-16
Thanks so much, Favux! I haven't gotten to check and see if my tablet is working yet, but the file is made. I'm hoping I don't need to do too much refining but I saved the before and after output as you suggested.

mystmaiden

edited to add - it seems to be working fine, I'll probably know more when I do some serious drawing. One question though, do I need to unmount or shut down Ubuntu to unplug the tablet? 

thanks again

---

### Post by Favux on 2009-08-16
Hi mystmaiden,

Your welcome.  You shouldn't need to, that's one of the things HAL/.fdi is about, usb hot plugging.  You should be able to unplug and plug in as desired.  But I think someone said pulling the tablet crashed things, so maybe a aiptek driver bug?

---

### Post by mystmaiden on 2009-08-17
When I unplugged it restarted Ubuntu, thought maybe I'd done something wrong. I think the trick will be to wait until shut down  and try to remember to unplug before start up so the usb doesn't hang up the works. 

mystmaiden

---

### Post by Favux on 2009-08-17
Hi mystmaiden,

Right, unplugging leads to a restart, that was it.  You could search launchpad and see if there is a bug filed against the aiptek driver for this.  If not you could file one.  There must be some problem with the usb driver.

---

