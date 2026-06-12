---
title: "second administrator user cant use synaptic"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by HwH on 2007-07-19
Im using feisty fawn and i have two accounts on my computer, one is the one i create whenever i install a new ubuntu version as my main user, the second is the user i use all the time.

I have set my second user to be administrator, given it all the administration rights i think.

But for some reason when using synaptic or anything like that to download new programs it cant connect:

[quote="error"]W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/liba/libart-lgpl/libart-2.0-dev_2.3.17-1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/liba/libart-lgpl/libart-2.0-dev_2.3.17-1_i386.deb)
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)[/quote]

I can use the internet on the second account, i can use synaptic on my 1st account but this one refuses to connect.

Any ideas why this is happening?

Thanks in advance

---

### Post by AlexenderReez on 2007-07-19
i think you are using tor right?that is not administration privilege problem...when you enter sudo apt-get install <package>,then enter password..it is mean there is nothing wrong with your privilege ....i think it is cause from server problem or maybe tor itself(if your are using tor) ...re download it...and if you can connect to internet by using web browser ...there is internet problem there:)

---

### Post by HwH on 2007-07-19
tor?

I can use internet and my other account can use synaptic and it has no problems, but it is annoying to have to log-out then log-in just to download one program.

---

