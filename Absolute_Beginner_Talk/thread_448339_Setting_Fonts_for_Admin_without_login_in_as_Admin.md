---
title: "Setting Fonts for Admin without login in as Admin"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by shuttleworthwannabe on 2007-05-19
As user I go to System>Preferences>Fonts and set my preferred fonts. However, when I evoke admin tasks e.g. synaptic, the fonts are set for admin, and so do not feel and look the same as user.

How do I set the fonts for admin while logged in as user, I wish to acces the same System>Preferences>Fonts, but for admin.

Thanks for the help,

swb

---

### Post by jordanmthomas on 2007-05-19
```
gksudo gnome-font-properties
```
Put in your password if prompted

You'll get an error about there already being a settings daemon running (there is, it's yours) but you can ignore it and set the fonts as you please.

---

### Post by shuttleworthwannabe on 2007-05-19
Thanks Jordan, I am afraid it did not chnage the fonts as desired; It opens the dialogue box and allows me to set the fonts. I close and logout login, but synaptic still has the previously set fonts.

Do I have to reconfigure something. like fontconfig??? Reboot??

Thanks

swb

---

### Post by jordanmthomas on 2007-05-19
hmmm...perhaps the best thing would be to set up a .gtkrc-2.0 for root  (I guess I was wrong about the settings daemon...it must only read those settings for one user)

```
gksudo gedit /root/.gtkrc-2.0
```
Put this in there
```
style "roots_font" {
  font_name = "[COLOR="Red"]cure 8[/COLOR]"
}
class "*" style "roots_font"

```
...obviously, changing out cure 8 for the font you want to use.
If you want to set different fonts for different gtk parts, you'll need to read about .gtkrc-2.0
I don't know too much about it, unfortunately

**edit**
this gets the "works for me badge" as I just tried it.

---

### Post by shuttleworthwannabe on 2007-05-19
Jordan, I rebooted and the desired fonts are now set for admin. I guess this is one time when reboot is necessary...

As for your second suggestion, I will keep this safe in case I have to use it later. You are a star! Thanks.

PS: How does one get to learn to code like this? I would have never figured this out on my own?

---

### Post by jordanmthomas on 2007-05-19
I learned about gtkrc when I started using fluxbox and all my gnome programs were ugly.  I still don't have it committed to memory and any time I mess around with one I still need to fire up google to find an example to edit.

So I guess the answer is experience.  The longer you use something the more you are kind of forced to learn about it.

---

### Post by shuttleworthwannabe on 2007-05-19
This is off topic, of course. I totally agree with the experience thing. 

However, there has got to me a book on how to of the tips and tricks with linux using code.

---

### Post by jordanmthomas on 2007-05-19
```
man
```
is often-times just the book you need.

Want to know more about cp (copy command)?
```
man cp
``` and you're up to your ears in options
...and so on

---

### Post by shuttleworthwannabe on 2007-05-19
great, thanx

---

