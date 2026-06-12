---
title: "[SOLVED] looking for a free php image upload"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-03-06
I'm trying to add an image upload to my site. I'm running my site on a LAMP server. can someone please help?? i've been looking pretty much non-stop since yesterday for one that actually works...:(

---

### Post by mevets on 2008-03-06
i wrote an imageshack clone when I first started to teach myself PHP. Direct link to tarball is [http://www.stevemcc.mevets.com/files/roundup.tar.gz](http://www.stevemcc.mevets.com/files/roundup.tar.gz) . Its not going to be something you find in the ubuntu repos or a deb for, remember this is just a learning project I took on.

It requires mysql it keep track of data on pictures, so this project may require more configuration than you care to hastle yourself with. If so, you can either look at upload.php inside the tarball and thats an okay template for uploading images (you would have to modify it for your on use) or you can just steal a script google finds when you search for php image upload

---

### Post by RadiationHazard on 2008-03-06
dude that sounds amazing.
but i'm going to be totally honest
i haven't really started learning php yet
i plan on starting soon
but what i'm looking for is more like a download it
unzip it
and put it into my site directory..

---

### Post by mevets on 2008-03-06
do you mean you want to have a script on your server that you tell  url to some image on the web and it steals it and puts in it a folder on the server? Sort of like a site to site download I guess.

---

### Post by Dr Small on 2008-03-06
I wrote this script:
[http://php.8ez.com/drsmall/base64/](http://php.8ez.com/drsmall/base64/)

and if I gave you the source, you could use it as an upload script, instead of a BASE64 encoder :)

---

### Post by RadiationHazard on 2008-03-06
that looks good to me.
could you set it up to be an image upload?
because if you could it looks nice and simple and exactally what i'm looking for!
:)

---

### Post by Dr Small on 2008-03-06
Actually, it is an image upload, but it deletes the image once it is converted to base64.

But, I'll dig up the source for you, and you can fool around with it, and help yourself learn Php :)

Dr Small

---

### Post by RadiationHazard on 2008-03-06
alright thank you so much!! :)
so will you just be supplying a link for me to download it in this thread?

---

### Post by Dr Small on 2008-03-06
Ya, here it is. I had to dig it up :)

---

### Post by RadiationHazard on 2008-03-06
it works!! =]
but i taught you where going to fix it to where it just gave the url?
and not base 64? :(
hahaha

---

### Post by Dr Small on 2008-03-06
No, I never did that. I just gave you the source of that application :)
It's very simple, and if you play around with it, you can customize it into whatever you want, which will improve your Php skills.

Dr Small

---

### Post by RadiationHazard on 2008-03-06
can someone please fix the uploader to where it just gives the url and not it in base 64? :(
I'm trying but i keep getting errors :(:(:(
please someone help me!

---

### Post by Dr Small on 2008-03-06
There..... I just went ahead and took all the base64 encode functions out of it.
Please go back a page and re-download the attachment.

Dr Small

---

### Post by RadiationHazard on 2008-03-06
thank you!
and that's actually probably more help to me
because i can compare them and see what you did and how it affected the out come
but really thank you so much!! i really appreciate it!

---

