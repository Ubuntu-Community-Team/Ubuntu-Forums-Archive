---
title: "2 quick questions about bash"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by rbgCODE on 2006-06-12
I searched google but i think I am searching wrong.  I am trying to write a bash script that asks questions like Name:

and then writes multiple lines into a text file like a conf file.

any help would be great

---

### Post by IYY on 2006-06-12
This is very simple. To read output, use the command "read" and to print to a text file, use redirection (>) and echo. Here's a sample script you can try:

#!/bin/sh
echo "Enter name:"
read name
echo "Enter number:"
read number
echo $name $number >> conf.txt

See what it does!

---

### Post by rbgCODE on 2006-06-12
Yes that does work, I was trying to do 

cat << _EOF_
Username=$USERNAME >> txtFile
Other
other
other
_EOF_

so I wouldnt have to write echo 800 times but thanks.

---

### Post by rbgCODE on 2006-06-12
if anyone could help me with this script I would be thankful, I am trying to automate some installing and editing of conf files for some friends and am only running into small problems..  n00b problems if you would.

Please email or IM would be best, or to create a record for other people forums are fine too :-p  pretty please.

---

### Post by uzi09 on 2006-06-12
a good site to refer to is:
[www.linuxcommand.org](www.linuxcommand.org)

teaches u EVERYTHING about bash scripting :D

---

### Post by rbgCODE on 2006-06-12
I read through that site but I am still having problems.

---

### Post by IYY on 2006-06-12
Ask me on MSN.

---

### Post by rbgCODE on 2006-06-13
Anyone else that could possibly help me?

---

