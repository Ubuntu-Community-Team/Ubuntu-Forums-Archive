---
title: "Outputting a text file?"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by meniscus on 2006-10-04
Ive installed a package called smartmontools and i am attempting to write the op to a file in my home directory.

With the command

> $sudo smartctl -a /dev/hda

evrything works fine. Its ops the info to the terminal


When i type 

```
$sudo smartctl -a /dev/hda > /Home 
```
It gives me an error...

bash: /Home: Permission denied

What am i doin wrong?

Thanks,
meniscus

---

### Post by Medieval_Creations on 2006-10-04
I'm not familiar with the probrgram your using but the syntax looks correct for creating an output file.

The only thing I can think of is that if that's exactly how you typed in teh command Linux is case sensative and /Home doesn't exist. 

> **meniscus said:**
> $sudo smartctl -a /dev/hda > /Home

I would try it like this and see if that works.
```
$sudo smartctl -a /dev/hda > /home
```
or
```
$sudo smartctl -a /dev/hda > /home/<your_user_name>
```

---

### Post by sumguy231 on 2006-10-04
/home alone shouldn't work either, you shouldn't have write permission to the top level directory. You need to use your home directory, which you can type quicker by using ~/<filename> (This means the file with name "filename" will be created in the current user's home directory.)

---

### Post by kvorion on 2006-10-04
You need to specify the name of the file that you want to create.

So say:
[programName] > path/filename

---

### Post by Ben Sprinkle on 2006-10-04
Try switching to root first:
```

sudo su
```
Also home is not "Home" it's "home". :)

---

### Post by sumguy231 on 2006-10-04
> **Goat Spirit said:**
> Try switching to root first:
```

sudo su
```
Also home is not "Home" it's "home". :)

That's fine if they really *want* to write to the /home directory, but I don't think that's what they want.

---

### Post by lamego on 2006-10-04
> **Goat Spirit said:**
> Try switching to root first:
```

sudo su
```
Also home is not "Home" it's "home". :)
You should not advise the person to use root specially to avoid an error he is not understanding.
The filename /Home means the file named Home on the / directory, a regular user should not create files on the root directory. 
An usual path for the file destination would be ~/file

---

