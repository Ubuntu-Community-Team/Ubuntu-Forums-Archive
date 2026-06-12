---
title: "connecting to internet"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by tollboy on 2007-12-03
yesterday i installed ubuntu on my laptop
before this i was using windows in which i directly connect to internet.
and in ubuntu i am nt able to do so even if i had entered this code [COLOR="Red"]pppoeconf[/COLOR]
it is nt connecting after doing 4-5 try.
please help............

---

### Post by OffAxis on 2007-12-03
does 
```
ifconfig
```
list a network card?

---

### Post by tollboy on 2007-12-03
i already tried it bt it is nt working 
ok wat shall i do after ifconfig
???????

---

### Post by OffAxis on 2007-12-03
```
i already tried it bt it is nt working 
```
What do you mean?

Does ifconfig come back with a card?

pppoeconfig depends on a network card being in place, if you don't have one installed (and detected correctly) it'll fail every time.

---

### Post by tollboy on 2007-12-03
can u tell me in sm more details 
when i give the comand ifconfig then in outcome 3 pera r coming

---

### Post by tollboy on 2007-12-03
wat i should make out of that
outcome

---

### Post by tollboy on 2007-12-03
this attached file is a screensht after running if config 
cn ni body help me after that

---

### Post by OffAxis on 2007-12-03
What kind of internet connection do you have?
DSL, cable modem, etc.
Make sure you have it hooked up before configuring.

You may be plugged into eth2.

try
```
sudo pppoeconf eth2
```

if that doesn't work try 
```
sudo pppoe-discovery
```

---

### Post by tollboy on 2007-12-03
i have airtel broadband conection
having 1 modem

---

### Post by OffAxis on 2007-12-03
since you've got a dsl connection don't forget about the line filters on the phones, fax machines, whatever else is plugged into the POTS (plain old telephone system) wiring. Anything that may be plugged in since you were last successfully connected could impact you (like a Tivo modem).

The **pppoeconf eth2** should hopefully get you there, if not the **pppoe-discovery** should tell you where it thinks the modem is.

---

### Post by tollboy on 2007-12-04
pppoe-discovery is not working
the outcoe id 
"Timeout waiting for PADO packets"
can anybody tell what is this PADO

---

