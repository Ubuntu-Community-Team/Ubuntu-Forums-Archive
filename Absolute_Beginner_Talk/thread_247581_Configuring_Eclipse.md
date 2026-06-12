---
title: "Configuring Eclipse"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by cjnkns on 2006-08-30
Hi! I was hoping I could request some assitance configuring elipseo in Ubuntu. I am using this guide (only doing the eclipse part though)
[https://help.ubuntu.com/community/EclipseWebTools](https://help.ubuntu.com/community/EclipseWebTools)

When I issue the following command
sudo chmod +x `sudo find eclipse -type d`

I get the following error 'cannot access 'sudo find eclipse -type d': no such file or directory.

I am in /opt and see the directory listed not sure what the problem is.

---

### Post by jpeddicord on 2006-08-30
Make sure that those backticks (`) are actually backticks, not quotes ('). You want the key on the top-left, the tilde (~) key.

---

### Post by cjnkns on 2006-08-30
HA! You're a genius!

---

### Post by cjnkns on 2006-08-30
I wans't trying to be sarcastic....hope it doesn't sound that way...

Thanks for your help

---

### Post by cjnkns on 2006-08-30
Alright on more thing (I hope)..
I am attempting to do the part where I put the executable in my /usr/bin directory..
But whenever I attempt to do the sudoedit and then save it will not let me becuase it says I do not have permission. 
I have closed the terminals and tried a couple of times to issue the chomd 755 command but still no joy?


Thanks for you help..](*,)

---

