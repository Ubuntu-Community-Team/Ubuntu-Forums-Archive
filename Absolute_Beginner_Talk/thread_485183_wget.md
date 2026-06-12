---
title: "wget"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by quinnten83 on 2007-06-26
So, I'm trying to learn more about the commands in bash.
And I'm checking out wget as it is frequently used here.
as I understand if you use arguments -O it will output to a file.
My question is, can I use wget to automatically download a file that is on the internet and what arguments do I use to make it save what it has downloaded to a specific directory?
I ask here, because the man page is like a mile long.

i tried with the following code, to test
```
[darrell@darrell-laptop1:~$ wget -q http://thor.mirtna.org/oddities/lookalikes/pics/mario_-_ron_jeremy.jpg -O ~/Desktop
/CODE]

but got this response and no file on the desktop
[CODE]/home/darrell/Desktop: Is a directory
darrell@darrell-laptop1:~$ 

```

---

### Post by greg_g on 2007-06-26
You need to specify the output FILE, not just a directory.  So, your command should look like this:

```
wget -q http://thor.mirtna.org/oddities/lookalikes/pics/mario_-_ron_jeremy.jpg -O ~/Desktop/mario_and_ron_jeremy.jpg
```

As you can see I renamed the file also. 

Or, you can do this:

```

cd ~/Desktop/
wget http://thor.mirtna.org/oddities/lookalikes/pics/mario_-_ron_jeremy.jpg

```

That command just saves the file to the current directory, in this case ~/Desktop/

Hope that helps,

greg

---

### Post by quinnten83 on 2007-06-26
Ok, that makes it clearer, BTW sorry for the choice of file, I just grabbed something to try out with.
and thanks for the advise.

---

### Post by KIAaze on 2007-06-26
> **quinnten83 said:**
> BTW sorry for the choice of file
No, thank you for the choice of file. ^^

I had some fun on the corresponding [site]("http://thor.mirtna.org/oddities/lookalikes/").
Here are the funniests I found:
[http://thor.mirtna.org/oddities/lookalikes/pics/zerg_overlord_starcraft_-_flying_spaghetti_monster.jpg]("http://thor.mirtna.org/oddities/lookalikes/pics/zerg_overlord_starcraft_-_flying_spaghetti_monster.jpg")
[http://thor.mirtna.org/oddities/lookalikes/pics/ayane-01.jpg]("http://thor.mirtna.org/oddities/lookalikes/pics/ayane-01.jpg")
[http://thor.mirtna.org/oddities/lookalikes/pics/haku_kira_kujah_superman_-_chaos_xenosaga.jpg]("http://thor.mirtna.org/oddities/lookalikes/pics/haku_kira_kujah_superman_-_chaos_xenosaga.jpg")

---

