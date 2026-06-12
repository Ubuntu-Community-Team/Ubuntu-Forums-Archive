---
title: "Fans crazy fans =)"
date: 2010-10-06
forum: Apple Hardware Users
---

### Post by SuperMiguel on 2010-10-06
So im dual booting OSX and ubuntu, when OSX the fans run very quiet, and i cant hear them. As soon as i boot to ubuntu the fans go to 100% and get kinda loud any fix for this?

---

### Post by linuxopjemac on 2010-10-07
which mac ?

---

### Post by Freek07 on 2010-10-07
I would suspect the GPU.

First, check your temps- open your terminal and write "sensors".
You will get something like this, TG** is graphics stuff, TC** is CPU stuff:

applesmc-isa-0300
Adapter: ISA adapter
Left side  :4957 RPM  (min = 4964 RPM)
Right side :4957 RPM  (min = 4964 RPM)
TB0T:        +35.2°C                                    
TB1T:        +35.2°C                                    
TB2T:        +35.2°C                                    
TB3T:        +35.5°C                                    
TC0D:        +75.5°C                                    
TC0F:        +59.8°C                                    
TC0P:        +60.0°C                                    
TG0D:        +65.0°C                                    
TG0F:        +59.8°C                                    
TG0H:        +53.0°C                                    
TG0P:        +59.8°C                                    
TG0T:        +62.8°C                                    
TG1H:        +62.0°C                                    
TN0D:        +64.5°C                                    
TN0P:        +61.8°C                                    
TTF0:        +65.0°C                                    
Th2H:        +57.0°C                                    
Tm0P:        +58.2°C                                    
Ts0P:        +33.2°C                                    
Ts0S:        +46.8°C                                    


if it's graphics- Did you install nvidia proprietary drivers? If not, install them ([www.nvidia.com](www.nvidia.com)). Then you will be able to see PowerMizer stuff in graphics interface and put it into powersafe mode.

for CPU, right click on panel and add cpu frequency monitor. It shouldn't be always on max frequency- if it is, click the icon of freq monitor and select "powersafe" or "conservative" mode.

At the end of the day, it will never be as quiet in linux as in osX, but it will run much much much much faster :)

---

