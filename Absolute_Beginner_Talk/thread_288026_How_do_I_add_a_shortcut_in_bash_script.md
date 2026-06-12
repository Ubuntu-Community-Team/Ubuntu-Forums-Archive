---
title: "How do I add a shortcut in bash script?"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-10-29
I need help with scripting.  I was wondering if a shortcut can be added for stuff that gets repeated but only differs by a word.

Lets say the script contains
```

hello1=`echo hello tammy`
hello2=`echo hello timmy`
hello3=`echo hello tommy`

hi1=`echo hi tammy`
hi2=`echo hi timmy`
hi3=`echo hi tommy`

bye1=`echo bye tammy`
bye2=`echo bye timmy`
bye3=`echo bye tommy`

echo $hello1 $hello2 $hello3
echo $hi1 $hi2 $hi3
echo $bye1 $bye2 $bye3

```
How would I make a shortcut that acts like this
```

hello1=`echo hello tammy`
hello2=`echo hello timmy`
hello3=`echo hello tommy`

echo $hello1 $hello2 $hello3

[shortcut start]
Okay, now repeat what I just did above, but this time, replace the "hello" with "hi"
[shortcut end]

[shortcut start]
Okay, now peat what I just did above, but this time, replace the "hello" with "bye"
[shortcut end]
```

---

### Post by kidders on 2006-10-29
Hi there,

It's hard to figure out exactly what you want. How about something like this...

```

for i in `sed 's/\:.*//' /etc/passwd`; do
	echo Hello $i
done

```

... which, just for the sake of it, says hello to every user on your system. Is that any use to you?

---

### Post by tux101 on 2006-10-29
No.  Because saying hello is not the subject.  It is just merely a piece of example part of the subject.

I can recall saying "hello tammy" by simplying inputing $hello1, because I made it a shortcut with this
```

hello1=`echo hello tammy`

```

I would like to know how I can make this entire piece
```

hello1=`echo hello tammy`
hello2=`echo hello timmy`
hello3=`echo hello tommy`

echo $hello1 $hello2 $hello3
```
a shortcut.  But with the option of changing the a word, in this case, the "hello".

So let us assume it behaved this way
```

I=(
i1=`echo i1 tammy`
i2=`echo i1 timmy`
i3=`echo i1 tommy`

echo $i1 $i2 $i3)

i=hello

Now echo $I.
```

---

### Post by kidders on 2006-10-30
Hey again,

You could try replacing the word "Hello" in my example with "$1", and saving the script as /usr/local/bin/say. Then, you could try typing **say hello** or **say goodbye**.

I'm still not quite certain what the application could be. :confused:

---

