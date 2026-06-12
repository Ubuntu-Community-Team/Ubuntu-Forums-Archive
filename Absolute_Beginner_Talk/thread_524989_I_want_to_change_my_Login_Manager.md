---
title: "I want to change my Login Manager"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by CapitanYochua on 2007-08-13
How do I change my login manager on Feisty?

---

### Post by CapitanYochua on 2007-08-13
Nevermind. I figured it out.

---

### Post by kerry_s on 2007-08-13
sudo apt-get install (xdm,wdm,kdm)
or use synaptic if you want to do it by gui.

you also always have the option of just using startx.

my .bash_profile to auto start X after log in>

# starts gui                                                                    
if [ -z "$DISPLAY" ] && [ $(tty) = /dev/tty1 ]; then                            
startx                                                                          
fi

---

