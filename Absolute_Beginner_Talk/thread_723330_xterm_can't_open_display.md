---
title: "xterm can't open display"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by jatala on 2008-03-13
Hello :

I'm trying to export the display form a solaris 10 machine into muy kubuntu laptop. I had execute the following commands :

1.- From the konsole in my laptop:

# xhost +
#ssh -X solaris_machine.

2.- once I'm logged in the solaris machine I exported the display variable.
# export DISPLAY=my_laptop:0.0
#cd /usr/openwin/bin
#./xterm

./xterm Xt error: Can't open display: my_laptop:0.0

I'm new on ubutu and probably there are an easy solution, any suggestion?

Many thanks.

---

### Post by Dr Small on 2008-03-13
Try:
```
ssh -XC -c blowfish solaris_machine
```

Then just run:
```
/usr/openwin/bin/xterm
```

---

### Post by jatala on 2008-03-13
¡¡¡ many thanks it works !!!

---

### Post by soapytheclown on 2008-05-06
> **Dr Small said:**
> Try:
```
ssh -XC -c blowfish solaris_machine
```

Then just run:
```
/usr/openwin/bin/xterm
```

thankyou so much been tearing my hair out over this!! i could do it in windows but not in ubuntu.. till now!!! 

=D

---

