---
title: "unwanted transparency"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by parts-man73 on 2008-02-22
Certain programs (in peticular, EAGLE CAD) I get transparent foregrounds with. I found a couple threads from others asking for a solution to this problem, but so far have not found any solutions. The transparency makes it very difficult to use these programs and I am forced to do that work under Windows. 

Any ideas what might cause this? 

I shall be more specific. The Background is a solid white. I can increase/decrease the opacity of the background with alt-button5 and alt-button4. when the Backgound is almost fully transparent, it resembles the Foreground.

Is it possible, to and how do you, adjust the opacity of the foreground?

Thank you,
Brian

---

### Post by jordanmthomas on 2008-02-22
I am a little confused as to what exactly you're talking about.  Could you post a screenshot perhaps?  There's probably a setting in compiz we can change to fix it.

---

### Post by parts-man73 on 2008-02-22
Attached is a screenshot of Eagle, showing the transparency. Maybe it's black that is transparent. 

When the background is white, the foreground is transparent, 
When the background is black, it's the background is transparent

When I move the window over another window with a white background, the window turns all white.

I've played with all the "advanced desktop effects settings" that sound related, but nothing has helped.

---

### Post by jordanmthomas on 2008-02-22
Do you by any chance have the "color opacity" plugin enabled?
This looks like something it may have done.

---

### Post by jordanmthomas on 2008-02-22
Also, I found this.
[http://minipop.org/](http://minipop.org/)

Looks A LOT like what you are looking for.
Hope it helps.

---

### Post by parts-man73 on 2008-02-22
excellent! That worked! the command "export XLIB_SKIP_ARGB_VISUALS=1" made all the difference. 

He mentioned creating a script to launch that command before launching eagle. Is there a tutorial on making a script? I haven't done one before.

---

### Post by jordanmthomas on 2008-02-23
You can do this:
```
gksudo gedit /usr/bin/eaglefixed
```
And put this in it:
```
#!/bin/bash
export XLIB_SKIP_ARGB_VISUALS=1
exec eagle
```
Change eagle to whatever eagle's binary name is (likely just eagle)

Then, save it and close it.
```
sudo chmod +x /usr/bin/eaglefixed
```
Then, instead of running eagle run eaglefixed.

edit
Also, if you want to still just run eagle instead of eaglefixed, and you're filling a little brave, you can do this instead:
1.  rename the eagle binary to eagleold
2.  Name the script I gave you eagle instead of eaglefixed
3.  In the script, change exec eagle to exec eagleold

---

### Post by parts-man73 on 2008-02-23
Once again, Thank you. I did exactly that and everything works great now! 

I can use Eagle with Ubuntu!

Thanks,
Brian

---

### Post by linuxman on 2008-04-02
even better would be if you use this command:

exec eagle $1

than krusader, dolphin and so on will be able to open the file you click right away...

HTH

Tom

---

