---
title: "please help me restore my xorg backup"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by Jason Weiss on 2006-11-26
Please help me, 

i have been trying for ages to get my 5 button mouse and beryl to work on my edgy installtion. 

I am a nubie. 

Every time i mess around with xorg, I resart and come everything sort of crashes and I can only log in with cammand line mode. 

I am not so much asking for help with messing around with xorg, I am willing to use trial and error to resolve this.

The question I have is this, before I start messing around I create a back up of xorg.

How can I restore this back up?

To dat I have been just reinstalling ubuntu, but this time I am the middle of a good download of "lost" and I don't want to lose it again.

I know there must be a simple answer?

---

### Post by junglepeanut on 2006-11-26
an easy way is to save one as 

xorg.conf.IKnowthisworks

I actually do this. WHhenever I get one I like better then the rest I update it.

Then whenever I really mess things up.

```
cp xorg.conf.Iknowthisworks xorg.conf
```

just make sure you have path set correctly i.e. in home

```
cp /etc/X11/xorg.conf.Iknowthisowrks /etc/X11/xorg.conf
```

Also you can meander to the directory and 

```
ls -l
```

this will show you time stamps of all the versions created, so you can pick say the .orig if you want to go that far back.

---

### Post by bulldog on 2006-11-26
Instead of the mv [move] command,I should use the cp [copy] command.

So your original backup stays where it is stored for further use.

---

### Post by Jason Weiss on 2006-11-26
Ok I think i already have a backup of the file. how do delete the currupt one and use  the good one

---

### Post by junglepeanut on 2006-11-26
Aye, bulldog is right use cp, I have been using mv all day for my school work and made a mistake in this post.

Editing it.

---

### Post by junglepeanut on 2006-11-26
You probably need sudo too, of course, and this will just write over the bad one.

---

### Post by Jason Weiss on 2006-11-26
o i feel confused can anyone tell me what is the line of code I will need to use?

---

### Post by junglepeanut on 2006-11-26
```
sudo cp path_to_the_file/the_file_you_know_is_good /etc/X11/xorg.conf
```
i.e.
```
sudo cp /etc/X11/xorg.conf.Iknowthisowrks /etc/X11/xorg.conf
```

---

### Post by bulldog on 2006-11-26
> **Jason Weiss said:**
> Ok I think i already have a backup of the file. how do delete the currupt one and use  the good one

You don't have to delete anything just copy over it.
If you have the name of the copy just use this.
```
sudo cp /etc/X11/xorg.conf-???? /etc/X11/xorg.conf
```
where you should place the name of your backup instead of xorg.conf-????.

---

### Post by Jason Weiss on 2006-11-26
Thanks Jungle 

i will give it a go

---

