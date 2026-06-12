---
title: "Permission Denied in Terminal of Live CD"
date: 2012-03-04
forum: Apple Hardware Users
---

### Post by Javelin Dan on 2012-03-04
I'm trying to wipe the hard drive of an old  Mac G4 "Graphics" using an Ubuntu 10.10 Ppc live CD and the terminal command of "dd if=/dev/random of=/dev/sda". I simply get a line that says "permission denied". At no time am I asked for a password, but I entered the command "sudo passwd ubuntu" to set a new one and tried entering it first but it says "no command found". I'm obviously missing something basic here - could anyone fill me in? Any other suggestions appreciated.Thanks.

---

### Post by lindsay7 on 2012-03-04
You could us Gparted from the live cd and just reformat the partition in question,

---

### Post by snowpine on 2012-03-04
Use **sudo** before your dd command. :)

---

### Post by Javelin Dan on 2012-03-05
snowpine - I did as you suggessted and the command was accepted. Just for my continuing education, how long should it take to wipe a hard drive? I enetered the command and got a blinking cursor and let it run for over two hours and nothing changed. Not knowing if it was working or not, I got impatient and closed out. Before closing completely I got a message that a process was still running. Was I just too quick to pull the trigger?
 
lindsay7 - I then tried your suggestion and of course the partition was deleted in about 30 seconds. I do understand that the "dd" command wipes all traces of data where the G-Parted erase does not, but I was only trying to make space, not sanitize my hard drive. Thanks to both for responding.

---

