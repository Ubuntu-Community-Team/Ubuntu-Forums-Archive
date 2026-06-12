---
title: "Hamachi help!!!"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by DevyD on 2006-01-12
Hi there

I am trying to use Hamachi, a zero-configuration virtual networking tool. Under the "quick start" instructions it tells me to run the "make install" command from the root account, but I keep on getting error "make: command not found".

Can anybody please tell me how to solve this error, or what this error means?


Thanks

---

### Post by Joeb on 2006-01-12
You need to install the build-essential package which includes the compilers, make program and most other libraries you will need.  You can install it through the Synaptic package manager or from the command line with:

sudo apt-get install build-essential

---

