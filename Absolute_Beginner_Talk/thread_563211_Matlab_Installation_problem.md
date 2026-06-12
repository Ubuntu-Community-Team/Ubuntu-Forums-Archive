---
title: "Matlab Installation problem"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by gregkrc on 2007-09-29
I have searched and read everything I can find, but I am having a unique problem. When I run the installation for Matlab 7.1 R14 I make it through installing the program, but when it says to press continue to go on to activate the program, the screen closes and goes back to the terminal. I would REALLY appreciate any help.


My procedure:
I copied the MATLAB cd to a directory in /usr/local/matlab71_sv
I ran the "install_unix.sh" in the terminal 
it appears to install fine, but stops before activation :(




I found the solution in another thread. Basically you have to install gawk. Ubuntu by  default uses mawk which doesn't have the buffer. After installing gawk, I went in and changed wherever it used awk in /bin/activation.sh to gawk. And it works!!!!!

---

