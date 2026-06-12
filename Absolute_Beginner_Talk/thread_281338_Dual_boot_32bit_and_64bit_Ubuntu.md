---
title: "Dual boot 32bit and 64bit Ubuntu?"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by NoX33 on 2006-10-20
Can you dual boot both 32bit and 64bit Ubuntu? If so, how can I do this?

I have both 32bit and 64bit installed on separate partitions, however can't dual boot. Grub menu shows both 386 and AMD64 kernels, yet when I select AMD64, it loads the 32bit partition. I figured this, due to the fact that nothing works, no mouse or touchpad, no internet at all, and all the changes I made to the settings are the same where as 64bit is a fresh install. Also, 32bit doesn't show the AMD64 kernel installed in synaptics, but it is in the grub menu. Thanks.

---

### Post by ReaderRat on 2006-10-20
You must have a 64-bit machine first....AMD64, Dual-Core, etc...do you?

EDIT: You can run 32-bit on a 64-bit machine, but not vice-versa.

---

### Post by NoX33 on 2006-10-20
Yes, I have a 64bit machine. Everything is compatible too. I originally ran only 64bit Ubuntu, but when I upgraded to Edgy I had a problem that left me to reinstall. I want both on due to the limited programs on 64bit.

---

### Post by ReaderRat on 2006-10-20
You do need to keep your partitions separate - except for the /swap (only need one). I have read that you need different usernames & passwords on each partition, so linux doesn't get confused.

---

### Post by NoX33 on 2006-10-20
Is that all? It seems too simple to be just that. I have both on separate partitions. I have one swap and a separate partition for /boot and /home.

---

### Post by NoX33 on 2006-10-21
I have reinstalled 64bit on my computer with a different login name and password, but I still have a problem. I'm not sure that it the same problem just the other way around though. Loads right up when selecting AMD64 kernel. On 386 though, its loads to the second or third item on the start up list and then stops. Nothing else happens and the computer goes to a black screen and just stops.

---

