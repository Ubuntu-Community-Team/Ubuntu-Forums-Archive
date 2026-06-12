---
title: "Fax software"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by Bigadada_saba on 2007-03-14
I posted yesterday about fax software i tried efax   gfax  and another one bot i cant get them working with my hard vware can eny one tell me how to install them with apt and how to con figure the modem to wor with then.

---

### Post by Najand on 2007-03-14
The efax/gfax/kfax are all in Universe Repository of Ubuntu. If you haven't enabled Universe/Multiverse Repositories yet, go to:
"System => Administration => Software Sources"
And Check all options on the page with "Ubuntu 6.10" tab.
It will probably ask you your sources is out of date and will update them.
Then Close it and go to:
"Application -> Accessories -> Terminal"
And type there:
```

sudo apt-get update                            (Just In case it did not update them)
sudo apt-get install gfax                      (Change gfax with your favorite package name)

```
It will probably install efax or hylafax along with gfax.
After it was installed, type "gfax" in the terminal and push "Enter". You will find yourself in a really user friendly atmosphere and I think you can set it up yourself afterwards.

---

### Post by adam s on 2007-03-14
Have you got the correct drivers for your fax modem?

Have a look at this FAQ to help you [http://linmodems.org/](http://linmodems.org/) it may help you get set up.

Adam.

---

