---
title: "How to change back BERYL rendering platform?"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by fede82 on 2007-05-31
Hi,
I was playing around with beryl and I changed Rendering platform to FORCE XGL, and now the screen freezes just as I login because I had set beryl to start automatically.

Also, I`ve set ubuntu not to ask for my user id and login automatically as I turn on the system, so the only way I can boot is by choosing safe mode in grub.

How can I fix this?
is there any beryl configuration file I can edit to put the rendering platform back to automatic or nvidia?


thank you!!
:D

---

### Post by Vajra Vrtti on 2007-06-01
Try to rename ~/.beryl/settings to see if Beryl recreates it with default values.

```
mv ~/.beryl/settings ~/.beryl/settings.error
```

Beryl is still alpha software and I don't think it's a good idea to have it automatically started.

---

### Post by aldreis on 2007-06-01
I believe you'll need to edit a hidden file called **beryl-managerrc**, located in your home directory. 

To do that, you'll use **nano**, a handy command line editor. It's pretty easy. Login in safe mode ( as you already know how to do it ) and type this:

```
nano .beryl-managerrc
```

It will show something like this:

```

[wm-settings]
active_wm=0
fallback_wm=0
active_dm=0
iconsize=24
use_fallback_wm=true

[beryl-settings]
render_path=1
cow_mode=2
rendering_mode=2
platform=3
binding=2
no_gl_yield=true
```

The setting you want to change is **platform**, probably set at **3** ( XGL, as you said ).

Change it to **0** ( zero ) to go back to Automatic.

Then type CTRL+ O ( to save ) and CTRL+X ( to exit ). 

Now you could reboot, typing:

```
sudo reboot
```

Done ( I hope ). :-)

---

### Post by fede82 on 2007-06-01
thank you VERY much.
I´ll try it as soon as I get home.

thank you both again!

> **aldreis said:**
> I believe you'll need to edit a hidden file called **beryl-managerrc**, located in your home directory. 

To do that, you'll use **nano**, a handy command line editor. It's pretty easy. Login in safe mode ( as you already know how to do it ) and type this:

```
nano .beryl-managerrc
```

It will show something like this:

```

[wm-settings]
active_wm=0
fallback_wm=0
active_dm=0
iconsize=24
use_fallback_wm=true

[beryl-settings]
render_path=1
cow_mode=2
rendering_mode=2
platform=3
binding=2
no_gl_yield=true
```

The setting you want to change is **platform**, probably set at **3** ( XGL, as you said ).

Change it to **0** ( zero ) to go back to Automatic.

Then type CTRL+ O ( to save ) and CTRL+X ( to exit ). 

Now you could reboot, typing:

```
sudo reboot
```

Done ( I hope ). :-)

---

### Post by adampyre on 2007-06-06
Since the asker didn't reply I thought that I would mention that I was messing around with Ubuntu and ran into the same problem. Your solution worked! Thanks, Aldreis. 

One thing that this made me think of, is it would be nice if Beryl detected that there were problems and went back to a default state or previous state to work. Maybe I should suggest this on Beryls website, but if they ever look here, there it is ;)

> **aldreis said:**
> I believe you'll need to edit a hidden file called **beryl-managerrc**, located in your home directory. 

To do that, you'll use **nano**, a handy command line editor. It's pretty easy. Login in safe mode ( as you already know how to do it ) and type this:

```
nano .beryl-managerrc
```

It will show something like this:

```

[wm-settings]
active_wm=0
fallback_wm=0
active_dm=0
iconsize=24
use_fallback_wm=true

[beryl-settings]
render_path=1
cow_mode=2
rendering_mode=2
platform=3
binding=2
no_gl_yield=true
```

The setting you want to change is **platform**, probably set at **3** ( XGL, as you said ).

Change it to **0** ( zero ) to go back to Automatic.

Then type CTRL+ O ( to save ) and CTRL+X ( to exit ). 

Now you could reboot, typing:

```
sudo reboot
```

Done ( I hope ). :-)

---

