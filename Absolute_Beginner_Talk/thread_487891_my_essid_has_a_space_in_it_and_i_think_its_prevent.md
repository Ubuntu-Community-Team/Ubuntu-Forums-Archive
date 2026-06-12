---
title: "my essid has a space in it and i think its preventing me from connecting"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by kaboom on 2007-06-29
Hey all,
Im setting up my wireless connection to a local network and when i input 
```
 sudo iwconfig wlan0 essid "324 atwood" key ********
```

I get the output 
```
 Error for wireless request "set encode" (8b2a): invalid command ********
```

When I try without quotes around 324 atwood; it tells me atwood is an invalid command. Is there something In particular I need to do because there is a space in my essid? or is it a different mistake all-together?

Thanks
Chris

---

### Post by Metacarpal on 2007-06-29
try:
```
324\ atwood
```

Using a backslash escapes the space, causing it to be read as a literal part of the string.

---

### Post by kaboom on 2007-06-30
thanks for the reply.  I'm still getting the same error message with 324\ atwood.  any other ideas as to what it could be?

---

### Post by kaboom on 2007-07-01
how about this: could anyone tell me what "set encode" (8b2a) means?

---

### Post by p_quarles on 2007-07-01
You need to put a space between "324\" and "atwood".Alternatively, you could just change the router's ID to a more Linux-friendly name.

---

### Post by kaboom on 2007-07-01
> **p_quarles said:**
> You need to put a space between "324\" and "atwood".Alternatively, you could just change the router's ID to a more Linux-friendly name.


thanks for the reply.  In the original post, i thought it was a problem with the space, but after trying 324\ atwood (including a space between) i got the same error message.  my follow up posts were searching for other ideas on what could be wrong. so thats why I was asking if anyone knew what "set encode" (8b2a) meant

---

### Post by annda on 2007-07-01
if you are not using an HEX key try this

```
sudo iwconfig wlan0 essid "324 atwood" key "s:your_key_string"
```

--the "s:something" means the key is ASCI, not HEX

---

### Post by kaboom on 2007-07-01
> **annda said:**
> if you are not using an HEX key try this

```
sudo iwconfig wlan0 essid "324 atwood" key "s:your_key_string"
```

--the "s:something" means the key is ASCI, not HEX

ok i will try that, im connected in the library right now but I will post back whether it works.
thanks


edit: this may be a silly question but is there any way i would tell whether its a hex or ascii key?

---

