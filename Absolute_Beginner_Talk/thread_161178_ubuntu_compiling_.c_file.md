---
title: "ubuntu compiling .c file"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by danieljamestravers on 2006-04-16
hi all, 

i am having a problem with compiling a c file (catme.c). 
in ubuntu when i run the root terminal i try:

cc catme.c -o catme

(i get a response saying that the 'cc' command isnt recognized, so i tried...)

gcc catme.c -o catme

(still get the same response)



i dont know what to do (since im relatively new to the whole unix/linux/ubuntu thing).

can anyone please help?

thanks to you all for your replies in advance.

---

### Post by truNWA on 2006-04-16
I think when using -o you have to have a flie type on the end of the second name, like.....

gcc cateme.c -o catme.exe



yea that works for me

---

### Post by JoeMetal on 2006-04-16
That just means that you don't have gcc installed.  Go to Synaptics Package manager and install it.  It should then compile fine after that.

---

### Post by utab on 2006-04-16
sudo apt-get install build-essential

---

### Post by utab on 2006-04-16
[QUOTE=utab]sudo apt-get install build-essential[/QUOTE]


Sorry you are new, type this on the terminal window and then try again. This will install all the necessary compilers

Have fun with coding and g++.

---

