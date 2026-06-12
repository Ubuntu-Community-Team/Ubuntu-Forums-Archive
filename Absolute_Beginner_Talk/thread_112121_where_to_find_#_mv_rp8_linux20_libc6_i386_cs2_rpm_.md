---
title: "where to find # mv rp8_linux20_libc6_i386_cs2_rpm rp8_linux20_libc6_i386_cs2.rpm ?"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-01-03
to install realplayer
thank you

pat'

---

### Post by Perfect Storm on 2006-01-03
I'm not quiet sure what you want to do? .rpm files are for red hat or mandriva system. Why don't you grab realplayer from the repo? If you add PLF to your sourcelist.

---

### Post by phido on 2006-01-03
[quote=patrick295767]to install realplayer
thank you

pat'[/quote]

Download the realplayer*.bin worked for me.

---

### Post by patrick295767 on 2006-01-04
[QUOTE=phido]Download the realplayer*.bin worked for me.[/QUOTE]
  
I just would like to install this realplayer 
cos I did 
apt-get -f install realplayer and it asked me :
rp8_linux20_libc6_i386_cs2_rpm rp8_linux20_libc6_i386_cs2.rpm
... 
and I couldnt find it on the net.
  
  
Please, could you have a quick look to let me know where I can download the linux realplayer bin ? Sorry that I didnt make it yet to find realplayer for linux. 
  
I can only find for windows on the realplayer website.
  
Thank you very much,

Pat

---

### Post by Perfect Storm on 2006-01-04
add this to your sourcelist:

[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
#deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/b]

```

sudo apt-get update
sudo apt-get install realplay

```

It can't be easier ;)

---

### Post by patrick295767 on 2006-01-04
[QUOTE=Artificial Intelligence]add this to your sourcelist:

[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
#deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/b]

```

sudo apt-get update
sudo apt-get install realplay

```

It can't be easier ;)[/QUOTE]
  
Thank you very very much !!
(I'll try tonight)
  
Nothg to say, this forum and members are amazing !
  
2Artificial Int., my best wishes for this 2006 New Year !! 

Pat'

---

### Post by patrick295767 on 2006-01-04
[QUOTE=patrick295767]Thank you very very much !!
(I'll try tonight)
  
Nothg to say, this forum and members are amazing !
  
2Artificial Int., my best wishes for this 2006 New Year !! 

Pat'[/QUOTE]
  
Iam still with hoary on my server ... you'd have it for hoary then ? 
thank you 

pat

---

