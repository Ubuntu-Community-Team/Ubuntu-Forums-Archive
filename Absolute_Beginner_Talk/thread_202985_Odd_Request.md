---
title: "Odd Request"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by arsenic23 on 2006-06-24
When I'm working on something in Linux I tend to keep all the temp files on my desktop for easy access and whatnot.  So what I'm trying to do is make an alias that will do 
```
 rm ~/Desktop/* -vrd 
```

The thing is I'd like it to doulble check to make sure I want to do this.  -i makes it check before each file is deleted, and if I'm compiling there could be a ton of little files sitting all over the place.

Is there a good way to make an alias or some such thing that says, "Clear Desktop y/n ? " and then runs *rm ~/Desktop -vrd*  ??  

I've only been running linux for a few months so I'm still a little in the dark about scripting for the OS.

---

### Post by IYY on 2006-06-24
[QUOTE=arsenic23]When I'm working on something in Linux I tend to keep all the temp files on my desktop for easy access and whatnot.  So what I'm trying to do is make an alias that will do 
```
 rm ~/Desktop -vrd 
```

The thing is I'd like it to doulble check to make sure I want to do this.  -i makes it check before each file is deleted, and if I'm compiling there could be a ton of little files sitting all over the place.

Is there a good way to make an alias or some such thing that says, "Clear Desktop y/n ? " and then runs *rm ~/Desktop -vrd*  ??  

I've only been running linux for a few months so I'm still a little in the dark about scripting for the OS.[/QUOTE]

```

echo "yes/no"
read answer

if [ $answer = "yes" ]
then
        rm ~/Desktop -vrd
fi

```

---

### Post by arsenic23 on 2006-06-24
Thanks alot, I was able to get this working correctly with minimal modification.  

Here's one more question since I have this thread up already:
Where's a good resource to learn scripting for linux?  I'm asuming that since I use the sh command to run these kinds of scripts that they're ssh, or is that something different?

Thanks again

---

### Post by siccness on 2006-06-24
sh = shell
ssh = secure shell

A good source for BASH scripting, in my opinion is:
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)

---

