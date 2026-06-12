---
title: "make command"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by frogotronic on 2006-03-05
Hello,

I've just installed Ubuntu 5.10.  I have managed to switch the "root" account back to a traditional style root account.

I'm trying to get a version of the FPC software (from the Sanger Institute) to run on my version of LINUX (please correct my conceptual mistakes).

As I understand the instructions, I have to "make" the programme, or complile it for this variant/version of LINUX.  There is a "makefile" included from the authors of the programme.

Assuming that I've gotten the above correct, How do I execute the make command?  Do I need to be in the bin directory?  My programe is unzipped in the "/bin/FPC" directory.

Thanks

---

### Post by oscar on 2006-03-05
Open a terminal window and:
```
cd /bin/FPC
make
```

---

### Post by frogotronic on 2006-03-05
Hi,

I get an error.

"bash: make: command not found"

---

### Post by engla on 2006-03-05
This is an Extremely FAQ

You need 'build-essential' to compile source packages.

sudo apt-get install build-essential

---

### Post by frogotronic on 2006-03-05
Thankyou!

---

