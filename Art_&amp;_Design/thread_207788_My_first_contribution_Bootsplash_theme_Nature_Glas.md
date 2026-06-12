---
title: "My first contribution: Bootsplash theme: Nature Glass"
date: 2006-07-02
forum: Art &amp; Design
---

### Post by j.vimal on 2006-07-02
Hi
This is my first contribution to Opensource :) Even though it may not be an app :)
If you want to download the theme right away:

I have made this in photoshop. This is a Bootsplash theme, and can be converted to a fbsplash compatible theme by using 
```
bootsplash2fbsplash nature
```
AFTER unpacking the archive to 
```
/etc/bootsplash/themes
```
Two resolution pics are available. 
1024x768x32 and 1280x1024x32. 

This theme is a tribute to Mother Nature. Please dont tell me it looks more like a tribute to Vista! :D 

The background picture (a stock photo) has taken from scx.hu site, but it seems to be down now. 
The glass effect was done in Photoshop.

**There is a small problem with the theme, and I would like some help in that regard.**
The progress bar was made to look glassy by using a small hack. Make the background effects in Photoshop and tell the fbsplash to paint over it in plain blue colour at a certan alpha (50% is what I have used here).
But, it has taken my configuration as a gradient, and slowly, the blue progress will disappear. When you shutdown, it comes back to the blue state.

[B]
Another problem
[/B]
I don't know where I can edit the colours for the VTs. Luckily, the default output colour is Grey, so, You can read what you type. But, manpages, and other stuff that use white colour wont work. I would appreciate if someone tells me how to do this too :)

Also, I have put the Debian logo, the grand-daddy of OSes like Ubuntu, Knoppix etc. I mean no harm! I will provided the PSD images too, incase you want to change those logos to Ubuntu.

Please use this theme in 32bit mode.
And, if you find the VT is clipped to a space much smaller to your expectations, again, you are welcome to edit the PSD file yourself! (EDIT: I didnt upload it here, as it is a hefty file. If you want i will mail it to you. Please send me a mail...)

Link to download:
[http://www.cs.iitm.ernet.in/~jvimal/blog/bootsplash-nature.tar.bz2](http://www.cs.iitm.ernet.in/~jvimal/blog/bootsplash-nature.tar.bz2)
Screenshot of the VT1
[http://www.cs.iitm.ernet.in/~jvimal/blog/bootsplash1.png](http://www.cs.iitm.ernet.in/~jvimal/blog/bootsplash1.png)
Screenshot of Silent mode (progress=0)
[http://www.cs.iitm.ernet.in/~jvimal/blog/bootsplash2.png](http://www.cs.iitm.ernet.in/~jvimal/blog/bootsplash2.png)

Note: Both screenshots are 1280x1024 resolution...
Note: I dont have the scrollbar working for 1024 resolution :( I have some work now, and I will get back to it whenever I have more free time.

For Opensource
Cheers
Vimal

---

### Post by metathran on 2006-07-06
Your bootsplash is amazing i saw it yesterday on gnome-look.org !
On gnome-look you said that there is a problem with 1280x1024 res ? Have you fixed this ?
I also don't understand how we should install it. I don't have any bootplash folder in my /etc/.

---

### Post by j.vimal on 2006-07-07
Hi
Glad that you liked it.
Now,
1. You should have installed fbsplash / bootsplash. I dont know how to do bootsplash, but there is a fbsplash guide in this forum. The title has the word "fbsplash", so, a search would bring it up.
2. Follow those instructions very carefully, and you will have fbsplash working. Once you have it working, run the commands I had given: 
First unpack the theme to /etc/bootsplash. Doesnt matter if the folder is not there, this is because bootsplash2fbsplash will search for installed themes here.
Then...
```
bootsplash2fbsplash themename
```. 
Now you should have your theme converted to fbsplash version, and copied to this folder:
```
/etc/splash
```

Then update your initrd, using
```
sudo update-initramfs -u
```

That is it! Then, specify the theme properly by passing arguments to the kernel. 
Remember, first follow the "fbsplash how" to guide!

here is a direct link anyway:
[fbsplash how to]("http://ubuntuforums.org/showthread.php?t=178439")

I have also uploaded a Debian-OSX theme. Do check it out! Plain and simple.
Cheers
Vimal

---

### Post by j.vimal on 2006-07-07
> **metathran said:**
> 
On gnome-look you said that there is a problem with 1280x1024 res ? Have you fixed this ?

Well, do look at it! It is actually not a problem, but something wierd :)
There is also a cloud shaped like debian in the pic... find out :)

---

### Post by Artificial on 2008-01-08
How can you set the resolution to 1280x1024x32? I can only see the 795 code for 1280x1024x!24! Is there any other way to acchieve this using grub? What do you suggest?

---

### Post by smartboyathome on 2008-01-08
I don't know about bootsplash or fbsplash, but I would like to see a splashy version of this. :)

---

