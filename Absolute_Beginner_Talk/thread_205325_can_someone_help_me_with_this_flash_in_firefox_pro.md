---
title: "can someone help me with this flash in firefox problem?"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-06-28
since i have installed ubuntu i havent been able to get sound to play consistently in firefox when i go to a site with flash such as youtube.com i reinstalled the flash plugin several times and it worked but only if i went to site 1st and had no other sound playing like in xmms but even then if i was in firefox for an hour and went to a flash page it would not play the sound.
So I had to restart several times.
i went googling and found this link to the ubuntuforums 
[http://www.ubuntuforums.org/showpost.php?p=1084235&postcount=5](http://www.ubuntuforums.org/showpost.php?p=1084235&postcount=5)

I followed the directions for the 1st part

sudo apt-get install alsa-oss
sudo nano /etc/firefox/firefoxrc

Already had alsa-oss installed
so i went to the second and changed :

change: FIREFOX_DSP="none"
to: FIREFOX_DSP="aoss"

as shown in the attachment

then I went to part 2

repeat for: /etc/mozilla-firefox/mozilla-firefoxrc

and typed

sudo nano /etc/mozilla-firefox/mozilla-firefoxrc

and got the second attachment

Did I follow the directions right? b/c I restarted n now get zero flash sound even after restarting the browser.

can someone correct me in this please?

---

### Post by Dr. Nick on 2006-06-28
Ive never done it that way so I am not sure if your doing it right or not, But their are 2 recent and ongoing threads concerning sound in flash that mention steps similar to that

[http://ubuntuforums.org/showthread.php?t=204022](http://ubuntuforums.org/showthread.php?t=204022)
[http://ubuntuforums.org/showthread.php?t=204804](http://ubuntuforums.org/showthread.php?t=204804)

Have you seen them yet?

---

### Post by maddbaron on 2006-06-28
nope checking thwm now

---

### Post by maddbaron on 2006-06-28
IT WORKED THANKS!

now i have a new question. u know how when u put in a cd one of the players starts automatically? 

well how can i make k3b my default cd burner/copier? i get sound juicer sometimes and its much slower than k3b. and i dont like gnome baker it gives me many errors n its also slow. k3b reminds of nero so i like it better.

and how can i make totem my default video player since it is the only one that plays most of the avi's and wmv i watch?

thanks in advance.

---

### Post by Dr. Nick on 2006-06-28
not sure on the k3b issue since I rarely use my cd drive ;)
but the totem instructions below may help somewhat.

If all the movies you watch are saved on your hard drive then just right click on one of each type and hit "properties" and look at the "open with" tab and just set it to "movie player" or totem, whichever you see

---

### Post by maddbaron on 2006-06-28
cool thanks.

---

