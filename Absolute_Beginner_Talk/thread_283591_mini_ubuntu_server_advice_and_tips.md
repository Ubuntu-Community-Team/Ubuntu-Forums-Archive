---
title: "mini ubuntu server advice and tips"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by bugboy on 2006-10-24
Hello all

New here on the ubuntu forum but have been looking at ubuntu for some time now.

Now i need some advice, help, tips and best procedures for a build i'm doing form my studio.

I would like to setup a ubuntu box that will act as a webserver(intranet) where i can build a test websites using php, MySQL, Ruby on Rails, smartfox socket server things like that. This will be closed off and only to be used on the internal network.

And also act as a file storage box as well. So either nfs or afs.

I already use my main machine (mac mini G4 OSX 10.3.9) as a webserver with php and MySQL but would like to use th ubuntu box instead.

I need to connect to it with three mac's mac mini, powerbook, ibook

Any help on where i should start what to look out for?

This would be great cheers

---

### Post by Bachstelze on 2006-10-24
Just install needed software (Apache, MySQL, PHP...) with apt-get/synaptic and you should be fine :)

Search the wiki for info about how to configure it.

---

### Post by bugboy on 2006-10-24
Cheers

I've looked at installing the LAMP server stuff then running a GUI. Tried webmin but seem to be overkill.

Would the server edition or normal install be better?

---

### Post by bodhi.zazen on 2006-10-24
> **bugboy said:**
> Any help on where i should start what to look out for?

This would be great cheers


[Ubuntu Server Guide](http://doc.ubuntu.com/ubuntu/serverguide/C/index.html)

---

### Post by Bachstelze on 2006-10-24
Whether you use a GUI or not changes *nothing* to the way servers will work. The main reason why "normal" server don't use one is simply because they don't need it. If you need one for whatever reason, just install it :)

Tip : installing the server edition and then installing the GUI manually with aptitude will make it easier to remove it later if you wish.

---

### Post by bugboy on 2006-10-24
> **bodhi.zazen said:**
> [Ubuntu Server Guide](http://doc.ubuntu.com/ubuntu/serverguide/C/index.html)

I have looked there but wanted to now what users had done as its all well and good reading but its not as good as hands on.

I installed a lamp server then a gui after and it worked well and apache2 running but its all locked out permissions and i need to file share to put the files on.

---

### Post by Klaidas on 2006-10-24
Well, you could install a server edition and then ```
sudo aptitude install ubuntu-desktop
```
Or, you could install the desktop edition and read [this]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by Bachstelze on 2006-10-24
The root Apache dir is /var/www, if you want to easily put files in it, you can CHMOD it so you have write access and the create a symlink to it in your home dir. that's what I've done on mine, anyway.

**@Kladas**, as I stated earlier, using aptitude instead of apt-get for huge metapackages like this makes life waaaay easier if you want to remove them.

Nice pics, by the way :) I don't like the "digital camera" style that much - too bright colors - but your technique is pretty good.

---

### Post by bugboy on 2006-10-24
i know how to CHMOD in mac OS X but how do you it in ubuntu?

---

### Post by Klaidas on 2006-10-24
@HymnToLife 
Opps, I forgot :| I usually just install them and got used to apt-get. I guess you're right, aptitude is a better command at this situation :)

And thanks for your review on my pictures :)

---

