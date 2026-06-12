---
title: "hello, a novice and need help"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by fouadaslam on 2007-10-29
hello 
Thanks for reading this post.
I am new to gutsy. i was installing java and somehow the process got interrupted. Now i get the error that has been mentioned here before "[COLOR="Blue"]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem[/COLOR]."
i did  a search and found several answers that i have tried but none of them works
i tried
sudo dpkg --configure -a
and then it says"[COLOR="Blue"]Setting up libc6 (2.6.1-1ubuntu9) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Bus error (core dumped)
dpkg: subprocess post-installation script returned error exit status 135[/COLOR]"

i tried sudo apt-get -f install
and
sudo apt-get update
sudo apt-get upgrade
however the same message appears "[COLOR="Blue"]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem[/COLOR]."
any help will be appreciated
thanks

---

### Post by speed145a on 2007-10-29
have you tried to **remove** the java package and try again?

---

### Post by fouadaslam on 2007-10-29
hi 
thanks for the reply
i cant access synaptic, as soon as i open it, the screen tells me to manually configure  dpkg  and leaves me no option but to close the window.

---

### Post by overdrank on 2007-10-29
> **fouadaslam said:**
> hi 
thanks for the reply
i cant access synaptic, as soon as i open it, the screen tells me to manually configure  dpkg  and leaves me no option but to close the window.

 Hi and , I would recommend check and make sure all your repos are enabled. System, administration, software sources. Then update in the terminal again and report any errors.

---

### Post by fouadaslam on 2007-10-29
> **overdrank said:**
> Hi and , I would recommend check and make sure all your repos are enabled. System, administration, software sources. Then update in the terminal again and report any errors.
hi,
every repo enabled, same message and same result in terminal
:(:(:(

---

### Post by hyper_ch on 2007-10-29
```

sudo apt-get --purge remove PACKAGE

```

You'll have to find out what java package you wanted to install.

---

### Post by Maestro23 on 2007-10-29
> **hyper_ch said:**
> ```

sudo apt-get --purge remove PACKAGE

```

You'll have to find out what java package you wanted to install.

Beat me to it.:)

---

### Post by fouadaslam on 2007-10-29
ok, will try this now
hope it works

---

### Post by overdrank on 2007-10-29
> **fouadaslam said:**
> hi,
every repo enabled, same message and same result in terminal
:(:(:(

Hi and I agree with the previous 2 post. Really flying blind here but you could try ```
sudo apt-get autoremove
sudo apt-get autoclean
```
And find the package name.

---

### Post by fouadaslam on 2007-10-29
sorry guys for the late reply
attempted every thing but the same message appears "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem"
is it always the case if a package gets interrupted ? i mean say if there is a power outage for a while, will this happen or is this a bug?
thanks for all the help, 
looking bleak

---

