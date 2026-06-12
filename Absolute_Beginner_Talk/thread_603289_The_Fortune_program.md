---
title: "The Fortune program"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Tombo5150 on 2007-11-05
How do i enable the offensive fortunes on my fortune program?

7.10 Gutsy user

---

### Post by mcduck on 2007-11-05
Run it with 'fortune -a' to get fortunes from all groups, including offensive ones. Or, if I remember right, with 'fortune -o' to _only_ get offensive fortunes.

---

### Post by Tombo5150 on 2007-11-06
I did that. The fortune -o command is still not working. It says no fortunes found.

---

### Post by nick_h on 2007-11-06
This is probably because no offensive fortunes are loaded in Ubuntu by default.  There are some fortune data files available as debian packages - [link](http://packages.debian.org/fortunes).

---

### Post by tormentum on 2007-11-06
Also, for a bit of fun, get a cow to say it:

cowsay `fortune -o`

(you may need to install cowsay: [http://www.nog.net/~tony/warez/cowsay.shtml](http://www.nog.net/~tony/warez/cowsay.shtml)

```
 _______________________ 
< Hello, bovine world!  >
 ----------------------- 
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
```

---

### Post by nick_h on 2007-11-06
I like it. :)

It is also in the universe repository.

---

### Post by Tombo5150 on 2007-11-06
Haha. I got the cowsay to work, but how do i know which package I need?

---

### Post by Billy_McBong on 2007-11-06
[COLOR="Blue"]heres a script that picks a random fortune and a random cowsay image[/COLOR]
```
#!/bin/bash
if [ !$COWPATH ]
then
	COWPATH='/usr/share/cowsay/cows/'
fi

cow_file_length=`ls -1 $COWPATH | wc -l`

RANDOM=$$ # initialized the random seed with the process id of this script
let "random_line = $RANDOM % $cow_file_length + 1"
cow=`ls -1 $COWPATH | head -n $random_line | tail -n 1`

/usr/games/fortune -a | cowsay -n -f $cow
```

---

### Post by Tombo5150 on 2007-11-07
I meant the package from that link above so that i can get the offensive fortunes. sorry cowsays works great

---

### Post by mcduck on 2007-11-08
> **nick_h said:**
> This is probably because no offensive fortunes are loaded in Ubuntu by default.  There are some fortune data files available as debian packages - [link](http://packages.debian.org/fortunes).

They are in Ubuntu's repositories also. Just 'sudo apt-get install fortunes-off' (or use synaptic and get the other fortune packages you might want..

It's always a good idea to check Ubuntu's own repositories before jumping to Debian or random web pages..

---

### Post by Tombo5150 on 2007-11-08
Nice, thanks a lot for that. I feel dumb for not checking in the first place but now I know better. Thanks again

---

