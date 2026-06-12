---
title: "echo &quot;Linux Terminal Communication Thread&quot;"
date: 2010-04-18
forum: Cafe Games
---

### Post by tyblogger5 on 2010-04-18
```
tyblogger5@ubuntuforums.org:~$ echo "Welcome to the LTCT thread, the challenge is to communicate all using Linux Terminal Commands (the more non-echo commands, the better)"
tyblogger5@ubuntuforums.org:~$ write "Your turn" nextuser
```

---

### Post by WitchCraft on 2010-04-18
```

root@IS1300:~# who
root     tty7         2010-04-18 14:45 (:0)
root     pts/0        2010-04-18 21:03 (:0.0)
root     pts/1        2010-04-18 21:06 (:0.0)
root@IS1300:~# echo "Hello World" | write root pts/1

Message from root@IS1300 on pts/1 at 21:08 ...
Hello World
EOF
root@IS1300:~# 

```

echo "Can one also use this to send a message to a user on a remote computer?"

wget -qO- [http://linux.byexamples.com/archives/233/write-a-message-to-login-users-through-terminal/](http://linux.byexamples.com/archives/233/write-a-message-to-login-users-through-terminal/)  | cat

---

### Post by tyblogger5 on 2010-04-18
```
tyblogger5@ubuntuforums.org:~$ write "I don't mind, as long as it's a terminal" WitchCraft
tyblogger5@ubuntuforums.org:~$ sudo apt-get who
```

---

### Post by CompyTheInsane on 2010-04-18
```

root@cavalier2:~# sudo -u nextuser notify-send -i info "Test message" "I wonder who will get this notification"
root@cavalier2:~#

```

---

### Post by gzarkadas on 2010-04-19
```

libero@laptop:~/source$ cat <<< 'You are the root of all evil!' | mail -s Testimonial root@localhost

```

---

### Post by tyblogger5 on 2010-04-22
```
tyblogger5@ubuntuforums.org:$~ rm /mnt/WindowsPartition/Windows/System32 --recurisve
tyblogger5@ubuntuforums.org:$~ echo "I love VBox!!!"
```

---

### Post by nerdopolis on 2010-04-22
```
nerdopolis@nerdopolis:~$ man you 
```

---

### Post by gzarkadas on 2010-04-23
The good old phrase typically spit off when someone wants people to follow instructions...:).
```

printf '\n%s %s %s %s!\n\n' $(help read | head -n 1 | cut -c1-4 | tr 'r' 'R') $(help read | head -n 1 | cut -c1-4 | tr 'r' 'R' | cut -c2-4 | tr 'da' 'th' | sed 's/./\n&/g' | tac | head -n3 | tr -d '\n') $(echo 'foo' | sed 's/[^f]/&&/g' | cut -c1-4 | tr 'o' '.') $(cut -c4-10 <(man me 2>&1))

```[B]
Note:[/B] [COLOR=Blue]The above expanded with backslashes to make it slightly more readable:[/COLOR]

printf '\n%s %s %s %s!\n\n' \
$(help read | head -n 1 | cut -c1-4 | tr 'r' 'R') \
$(help read | head -n 1 | cut -c1-4 | tr 'r' 'R' | cut -c2-4 \
  | tr 'da' 'th' | sed 's/./\n&/g' | tac | head -n3 | tr -d '\n') \
$(echo 'foo' | sed 's/[^f]/&&/g' | cut -c1-4 | tr 'o' '.') \
$(cut -c4-10 <(man me 2>&1))

---

### Post by nerdopolis on 2010-04-26
```
echo "/dev/null thats just AWSEOME"
echo "maybe mine should have been this before:"
man you || echo "back of the line"
echo " "
echo -e "but it will be hard to beat \033[1mgzarkadas'\033[0m post"

```

---

### Post by gzarkadas on 2010-05-02
```

cat <<< 'Please, post some nice terminal commands here!' \
     | $(cat /etc/passwd | awk -F: '{if ($3<1000) print $1}' \
     | sort -u | grep -P '^ma' | grep -P $(cat <<< 'kill' | tr -sd 'k' 'l' ) ) \
     -s 'Warning: thread activity is low' \
     -c root@localhost \
     all-members@localforum

```(the cc: is to guarantee that at least one person will receive the message if you run this :))

---

### Post by thomas144 on 2010-08-09
```
echo 'It looks like this thread went down a black hole, just like this data' > /dev/null
```

---

### Post by gzarkadas on 2010-08-10
```

alias woman=man && printf "$(seq 1 7 | sed 's/./%s/g' | tr '\n' ' ')\n" \
"$(man thread|head -n 1|cut -c1-7)" \
"$(woman come 2>&1|awk '{print $5}')" \
"$(paste /dev/null /dev/quantum-theory 2>&1 | awk -F: '{print substr($1,4,1) RS substr($2,8,1) RS substr($3,3,1)}' | tac | tr -d '\n')" \
"$(from|head -n1|cut -c1-4|sed 's/F/f/')" \
"$(info white 2>&1 | tail -n 1 | awk '{print substr($5,2,5)}')" \
"$(man bzexe | grep relies | awk '{print $2}' | cut -c1-5)" \
"$(woman sundancer2|grep Reverse|awk '{print $3}')"

```> Threads come out from white holes occasionally.


All that's needed is a small quantum leap ;). Come on everybody, spin your energy fields :D!

---

### Post by gzarkadas on 2010-09-12
```

man what 2>&1 \
  | sed -e 's/^[^m]*-\2\./' -e 'p' -e 's/./\n&/g' \
  | tac | tr -d '\n' \
  | sed 's/\(.*M\)\(M.*\)/\2\|\1\n/'

```> Manual Re-entry.|.yrtne-eR launaMIt is true that in order for humans to fly they must go to the terminal.

(an:lol:nym:lol:us)

---

### Post by gzarkadas on 2010-09-30
```

apropos linux terminal communication thread | grep -P '^(chattr|ip)' | tee \
    >(head -n1 | cut -c41-42 > ./1234-chars-first-part) \
    | head -n2 | tail -n1 | cut -c45-46 > ./1234-chars-second-part \
; paste ./1234-chars-[fs]*-part | sed 's/\t//' && rm ./1234-chars-[fs]*-part

```

[SIZE=4]bump[/SIZE]

---

