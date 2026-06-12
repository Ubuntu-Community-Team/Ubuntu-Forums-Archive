---
title: "pommed in 8.10"
date: 2008-10-29
forum: Apple Hardware Users
---

### Post by Debilski on 2008-10-29
Hi,
although the brightness keys and sound keys seem to be working out of the box with 8.10 on an MB 3.1 (ok, not really out of the box &#8211; brightness keys work only every other reboot &#8211; hopefully the mactel-fix is going to help), I find there are some issues that had not been there when using pommed.

First is that &#8211; at least in xfce; haven&#8217;t checked in kde or gnome &#8211; when I&#8217;m accessing a menu it is impossible to use the brightness or sound keys. This is rather annoying when you want to quickly turn off the music or something. (Also, when in terminal, one can see that the cursor loses focus for a small moment. I don&#8217;t know if this can have any side effects sometime.) I think that with pommed, one could use the button whenever one wanted to.

The other thing is that F10 does not mute the volume but sets the volume to zero, which means that you have to F12 all the way up again to have it as it&#8217;s been before. Also the step size could be smaller as far as I&#8217;m concerned. Is it possible to change this actually?

Another thing I just found out: It&#8217;s not only that F10 sets the volume to zero, it also resets whether the internal speakers had been turnd on before or not. So when you&#8217;re using headphones, press F10, then press F12 to restore the volume, you&#8217;ll find that the internal speakers are turned on again&#8230;


So, since with pommed I did not have these issues (and as a plus actually there was the volume symbol appearing when you pressed the volume buttons, so that you had an optical feedback when you used them) I wonder if and how it is possible to use pommed in 8.10?

Any ideas/suggestions?

Thanks

---

### Post by herzzreh on 2008-10-29
> **Debilski said:**
> Hi,
although the brightness keys and sound keys seem to be working out of the box with 8.10 on an MB 3.1 (ok, not really out of the box – brightness keys work only every other reboot – hopefully the mactel-fix is going to help), I find there are some issues that had not been there when using pommed.

First is that – at least in xfce; haven’t checked in kde or gnome – when I’m accessing a menu it is impossible to use the brightness or sound keys. This is rather annoying when you want to quickly turn off the music or something. (Also, when in terminal, one can see that the cursor loses focus for a small moment. I don’t know if this can have any side effects sometime.) I think that with pommed, one could use the button whenever one wanted to.

The other thing is that F10 does not mute the volume but sets the volume to zero, which means that you have to F12 all the way up again to have it as it’s been before. Also the step size could be smaller as far as I’m concerned. Is it possible to change this actually?

So, since with pommed I did not have these issues (and as a plus actually there was the volume symbol appearing when you pressed the volume buttons, so that you had an optical feedback when you used them) I wonder if and how it is possible to use pommed in 8.10?

Any ideas/suggestions?

Thanks


I had exactly the same issues in xfce, everything works as advertised in GNOME, I haven't checked KDE.

---

### Post by kosumi68 on 2008-10-29
> 
although the brightness keys and sound keys seem to be working out of the box with 8.10 on an MB 3.1 (
ok, not really out of the box &#8211; brightness keys work only every other reboot &#8211; hopefully the mactel-fi
x is going to help)


Although not the same model, this thread might help: [http://ubuntuforums.org/showthread.php?t=959992](http://ubuntuforums.org/showthread.php?t=959992)

> 
First is that &#8211; at least in xfce; haven&#8217;t checked in kde or gnome &#8211; when I&#8217;m accessing a menu it is impossible to use the brightness or sound keys. This is rather annoying when you want to quickly turn off the music or something. (Also, when in terminal, one can see that the cursor loses focus for a small moment. I don&#8217;t know if this can have any side effects sometime.) I think that with pommed, one could use the button whenever one wanted to.


With Hardy, the media keys never reached X, which is why it worked anywhere, anytime. The problems you currently experience are thus bugs, which should eventually be ironed out.

> 
So, since with pommed I did not have these issues (and as a plus actually there was the volume symbol appearing when you pressed the volume buttons, so that you had an optical feedback when you used them) I wonder if and how it is possible to use pommed in 8.10?


There is a volume symbol also in the Intrepid version - the graphics even depends on if you use metacity or compiz. If you dont see it, something else is wrong. To get pommed working, you would need to make sure the keys in question do not reach X. However, since most of the pommed application has been molded into various parts of the system, it really does seem simpler to try to make it work in this new gnome-controlled setup.

---

### Post by Debilski on 2008-10-29
> **kosumi68 said:**
> There is a volume symbol also in the Intrepid version - the graphics even depends on if you use metacity or compiz. If you dont see it, something else is wrong. To get pommed working, you would need to make sure the keys in question do not reach X. However, since most of the pommed application has been molded into various parts of the system, it really does seem simpler to try to make it work in this new gnome-controlled setup.

Ah, I understand; then this is mainly a problem with xfce, I guess. OK, I&#8217;ll wait then until it eventually gets fixed with the graphics.

And the problem with muting the volume is it fixed within Gnome or is this then a general problem with the soundmixer or whatever?

---

### Post by kosumi68 on 2008-10-29
> **Debilski said:**
> Ah, I understand; then this is mainly a problem with xfce, I guess. OK, I’ll wait then until it eventually gets fixed with the graphics.

And the problem with muting the volume is it fixed within Gnome or is this then a general problem with the soundmixer or whatever?

I have not looked into what part of the desktop actually responds to the volume keys, you guess is as good as mine. If you find out where the problem is, do tell :-)

---

