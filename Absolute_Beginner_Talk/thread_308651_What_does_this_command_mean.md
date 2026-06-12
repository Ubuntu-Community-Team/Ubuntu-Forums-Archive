---
title: "What does this command mean?"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by meniscus on 2006-11-28
Is the following a valid command?

my $temp=`/usr/local/sbin/hddtemp -n /dev/hda`;

and what does it mean?





The command ```
hddtemp -n /dev/hda 
``` returns the temperature of my harddrive

---

### Post by marx2k on 2006-11-28
Im not sure what 'my' would do, but $temp = etc etc

basically is setting up $temp as a variable to be used for functions inside a script.

At least as far as my knowledge of shell scripting goes :)

---

### Post by meniscus on 2006-11-28
But does it assume hddtemp is a folder or a command?

---

### Post by po0f on 2006-11-28
meniscus,

A command; in most shell scripting languages, backticks (`) surround commands that should be evaluated before the rest of the line, so in this case, the */usr/local/sbin/hddtemp -n /dev/hda* command is run, and the return value (the temperature), is stored in the variable $temp.

Is this Perl code that you got this from?  In Bash, you don't need to add the dollar sign to a variable's name to assign a value to it, but IIRC in Perl you do.

---

### Post by coder_ on 2006-11-28
Aye, that is Perl code.

---

### Post by jpeddicord on 2006-11-28
Yes, that would be Perl code. The 'my' at the beginning is required for declaring variables in Perl.

Basically, the commend sets $temp to the temperature of your HD.

---

### Post by meniscus on 2006-11-29
When i type it into the command line i get an error?


```
meniscus@meniscot:~$ /usr/local/sbin/hddtemp -n /dev/hdc
bash: /usr/local/sbin/hddtemp: No such file or directory
```

---

### Post by Arndt on 2006-11-29
> **meniscus said:**
> When i type it into the command line i get an error?


```
meniscus@meniscot:~$ /usr/local/sbin/hddtemp -n /dev/hdc
bash: /usr/local/sbin/hddtemp: No such file or directory
```

Then you need to install it first:

```
# apt-get install hddtemp

```

For me, it put itself in /usr/sbin, not in /usr/local/sbin.

---

### Post by meniscus on 2006-11-29
I had it installed alright. But as you corrctly pointed out it was in /usr/sbin, not in /usr/local/sbin. You re an absolute legend 

I was all day yest tryin to figure it out.  Cheers Bud

---

### Post by Arndt on 2006-11-29
> **meniscus said:**
> I had it installed alright. But as you corrctly pointed out it was in /usr/sbin, not in /usr/local/sbin. You re an absolute legend 

I was all day yest tryin to figure it out.  Cheers Bud

If you have (or think you may have) a program in your PATH, and just don't know where, you can do

```
$ which hddtemp
/usr/sbin/hddtemp

```

If it's not in your PATH, and perhaps not an executable file at all, try

```
$ locate hddtemp
```

---

### Post by meniscus on 2006-12-05
thanks

---

