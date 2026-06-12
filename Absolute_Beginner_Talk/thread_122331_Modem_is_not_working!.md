---
title: "Modem is not working!"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by Maskednightmare on 2006-01-27
I installed Ubuntu 5.10 For Your PC from the cds i got shipped from ubuntu.Everything is working fine except the fact that I have no internet connectivity at the moment.I have an Intel 536EP 56K internal modem installed in my pc.The device manager in Ubuntu displays this modem but does not detect it in Networking.I have tried using the method mentioned in [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto) but it is not working for sum inexplicable reason.I have downloaded all the packages as mentioned in the guide.But when i got to the step of Compiling the Driver, I faced a problem : 
First we need to uncompress the downloaded file. Start a terminal window and run the following command: 

 tar xzf Intel-536EP-4.71.tgz
This assumes you saved the file downloaded from Intel in your home directory; otherwise, type cd <directory-where-the-file-is> before typing the tar command above. 

This will create a directory Intel-536 with the source contained in it. Change to this directory by typing 

 cd Intel-536
Still in the terminal window, type the following: 

 make clean

(*this is where Im stuck, wenever i type in make clean, it says make : command not recognised*
Now what am I supposed to do?

---

### Post by lanef on 2006-01-27
hi,In the how to there is a section on gcc.did you download and install gcc 3.4?
but first open synaptic and install build-essential and linux headers.they are on
your breezy cd.then your make command will be active for compiling .

---

