---
title: "one last question lol"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-07-16
ok i finnally got this to work:

```

read option
case $option in		#start of choices
1 )  'jre/bin/java' client ;;		#runs endar client bitches XD

```

but what if i wanna do more then 1 command i put this but i dunno:

```

2 )  cd ../ ;;				#start of update process
     'files/jre/bin/java' WGet http://goat-spirit.com/Files/Endar-Linux.tar.bz2 ;;
     bzip2 -cd Endar-Linux.tar.bz2 | tar -xvf - ;;

```

---

### Post by Thirsteh on 2006-07-16
What you're doing there is piping. I'm supposing you just want to run two commands seperately on one line.

Use the '&&' operator.

ex: bzip2 -cd Endar-Linux.tar.bz2 && tar -xfv blablab && echo Hi

---

### Post by Ben Sprinkle on 2006-07-16
oke doke thx

---

