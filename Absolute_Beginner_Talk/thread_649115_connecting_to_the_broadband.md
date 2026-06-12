---
title: "connecting to the broadband"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by yvsmadhav on 2007-12-24
I use broadband(dial up) to connect to the internet. The modem is connected via the ethernet port. Unlike in Winxp where I just need to provide the username and the password to connect, I am unable to do the same in Ubuntu. I am an absolute beginner to the world of Ubuntu. Any help?

---

### Post by thelinuxguy on 2007-12-24
Did you try running sudo pppoeconf?
What is its output?

---

### Post by yvsmadhav on 2007-12-24
what is that? All that is greek and latin to me. Please provide a step by step guide to solve the problem.Thanks.

---

### Post by antmenj on 2007-12-24
Is it an ADSL connection?  You may be able to make your modem do the dialing for you rather than your computer having to do it.

What is the make / model of the modem?  That should answer the above question too if you dont know.

---

### Post by thelinuxguy on 2007-12-24
With regards to antmenj's post above, I will assume that you have an ADSL connection. Try out the following and let me know if it works.

Start a terminal. 
Applications >> Accessories >> Terminal

Type
```

sudo pppoeconf

```

You should get a blue screen with some output. Your ethernet card should be detected as shown by this line:
```

I found 1 ethernet device:
          eth0
...

```

Press Yes. The second screen should say:
```

Looking for PPPoE Access Concentrator on eth0...  

```

If it says that it can't find an access concentrator then you may have a problem and you will need to do some troubleshooting. However, if there are no problems you will be shown the next screen with output like this
```

 If you continue with this program, the configuration file
      /etc/ppp/peers/dsl-provider will be modified. Please make sure
      that you have a backup copy before saying Yes. 
...

```

Select yes and yes again. Now enter your username and password that you used to give in XP. Dismiss the remaining dialogs by selecting the relevant options. Select the default one if you don't know which one to select.

Now you can start the connection by typing
```

pon dsl-provider

```

To see the connection status, type
```

plog

```
It should show the IP address assigned to you and the DNS addresses.

To terminate the connection, type
```

poff

```

---

