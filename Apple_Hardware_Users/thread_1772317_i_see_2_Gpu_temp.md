---
title: "i see 2 Gpu temp"
date: 2011-05-31
forum: Apple Hardware Users
---

### Post by basoula on 2011-05-31
Hi boys! I have ubuntu 11.04 and i install sensors! But when i give "sensors" on terminal i look 2 temp from my Gpu! I use nouvau driver! 
Which of 2 is real?
```
basw@basw-HP-Pavilion-dv6700-Notebook-PC:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +44.0°C                                    

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +44.0°C  (high = +105.0°C, crit = +105.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +40.0°C  (high = +105.0°C, crit = +105.0°C)  

nouveau-pci-0100
Adapter: PCI adapter
temp1:       +65.0°C  (high = +100.0°C, crit = +110.0°C)  


```
my card in Nvidia Geforce 8400M GS
thanks for hepl!

---

### Post by cracker89 on 2011-05-31
nouveau-pci-0100
Adapter: PCI adapter
temp1:       +65.0°C  (high = +100.0°C, crit = +110.0°C)

Thats the one you want.

---

### Post by 3Miro on 2011-05-31
acpitz-virtual-0 is the sensor on your motherboard.

coretemp-isa-0000 and coretemp-isa-0001 are the two cores of your CPU.

nouveau-pci-0100 is your GPU.

The first number is your temperature, the high and crit are the numbers when the computer will start giving warning and potentially shutdown to prevent hardware damage.

---

### Post by basoula on 2011-05-31
thanks you very much for your help! I can see temp of my motherboard,that is very good! ;) Thank you both! =D>=D>=D>

---

### Post by cracker89 on 2011-05-31
"High five!"

---

### Post by basoula on 2011-05-31
sorry i'm from greece and i don't understand you! :(

---

### Post by cracker89 on 2011-05-31
:P my bad.. [http://en.wikipedia.org/wiki/High_five](http://en.wikipedia.org/wiki/High_five)

---

### Post by basoula on 2011-05-31
xaxaxaxa! now i understand you! Here we say "give me five" :p

---

### Post by cracker89 on 2011-05-31
Ah grammar huh. Each language has its own sense of it :) Stay well. Whats good greek food btw?

---

### Post by basoula on 2011-05-31
:P:P:P Greek food? well,souvlaki! [HTML]http://en.wikipedia.org/wiki/Souvlaki[/HTML]
it's the common food! And our soup call "fasolada" [HTML]http://en.wikipedia.org/wiki/Fasolada[/HTML] :):):)

---

### Post by cracker89 on 2011-05-31
lol.. I'm really going to have to see if I'm getting that anyplace close by.. :P Looks mouth watering. 

All the same, I can always try some cooking :P i think...

Cheers. Take care.

---

### Post by basoula on 2011-05-31
xaxaxa! ok! bye! kisses!

---

