---
title: "Frostwire 90% CPU Usage?!?"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by GSF1200S on 2007-03-30
What the hell is up with this? If Im running frostwire, my system monitor is showing one CPU using over 90%, with the other core around 50%!

I have an Intel Core2Duo at 2.16Ghz/ 667, and not that it matters but 2GB or RAM and a 667 FSB- I mean it doesnt seem like downloading a few video clips (2 to be exact) would be that demanding... Any ideas or is this just normal? I really dont like running my processor in the 90s..

---

### Post by STREETURCHINE on 2007-03-30
i dont know what the problem is or a solution but i dont really see a problem ,what else do you have running ,is your system crashing,my proccessor runs around 90%all the time with gimp editing photos and flock running also firefox on the go,your proccessor is there to be used not to sit idle,so unless it is crashing all the time i would not panic.

saying that someone may have a solution to try,to get it down

---

### Post by GSF1200S on 2007-03-31
> **STREETURCHINE said:**
> i dont know what the problem is or a solution but i dont really see a problem ,what else do you have running ,is your system crashing,my proccessor runs around 90%all the time with gimp editing photos and flock running also firefox on the go,your proccessor is there to be used not to sit idle,so unless it is crashing all the time i would not panic.

saying that someone may have a solution to try,to get it down

I understand what youre saying, but both cores bounce off 100%. On my buddies Window system it doesnt even clear 10% downloading 5 movies, whereas mine is using 100% d/ling 2 songs!! Somethings wrong here- hes got 1GB of ram with an intel core 2duo at 1.83 (553 ram and FSB), and Ive got 2GB of RAM, with an intelcore2duo at 2.16 (667 RAM and FSB). It doesnt make sense! Ive got to be missing something, here.

No matter what you say, it CANT POSSIBLY be good for a processor to sit at near 100% for hours... Last thing I need is to fry my processor dling a few songs.

---

### Post by STREETURCHINE on 2007-03-31
give us the output of 

```
top
```

no it will not hurt your processor it is doing what it is supposed to do if it was overheating and crashing all the time then yes you would have a problem

but i do agree it does seem a little high for what you are doing

---

### Post by GSF1200S on 2007-03-31
> **STREETURCHINE said:**
> give us the output of 

```
top
```

no it will not hurt your processor it is doing what it is supposed to do if it was overheating and crashing all the time then yes you would have a problem
 
but i do agree it does seem a little high for what you are doing

               PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
        19263 poeticrp  15   0  757m 102m  24m S  102  5.1   1:27.59 java               
        5311 root      15   0  331m  52m  12m S   17  2.6  13:23.15 Xorg               
    18316 poeticrp  15   0  170m  39m  20m S    3  2.0   1:09.51 rhythmbox          
    19384 poeticrp  15   0 62888  15m  11m S    1  0.8   0:01.35 gnome-system-mo    
     6359 poeticrp  15   0  321m 108m  29m S    0  5.4   4:40.20 firefox-bin        
              1 root      24   0  2912 1844  524 S    0  0.1   0:01.30 init               
              2 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
              3 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
              4 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
              5 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
              6 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
              7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
              8 root      10  -5     0    0    0 S    0  0.0   0:00.09 events/0           
              9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1           
            10 root      11  -5     0    0    0 S    0  0.0   0:00.00 khelper            
            11 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthread            
            35 root      10  -5     0    0    0 S    0  0.0   0:00.02 kblockd/0       

Java 102%?? Im guessing they are refferring to 100% of one core, but dang...

So whats the deal.. Is there another form of Java I can use? How about another p2p client that connects to the Gnutella network? I tried apollon but it sat at connecting forever.. The GTK Gnutella doesnt seem to return a lot of results.

---

### Post by GSF1200S on 2007-03-31
Sorry it didnt line up...

---

### Post by STREETURCHINE on 2007-03-31
that is ok  it never does ..as to the java well now i am lost, but if you are using edgy

install htop

                  ```
sudo aptitude install htop
```

it is better for this stuff.

 cpu are not my strong point but we will keep trying till some one with more knowledge comes along

what version of java are you running.?

---

### Post by GSF1200S on 2007-03-31
> **STREETURCHINE said:**
> that is ok  it never does ..as to the java well now i am lost, but if you are using edgy

install htop

                  ```
sudo aptitude install htop
```

it is better for this stuff.

 cpu are not my strong point but we will keep trying till some one with more knowledge comes along

what version of java are you running.?

Thanks for the help with this... processors arent the top of my knowledge either. Im glad ive got an Intel... All the athlons Ive had ran WAY hot, so naturally im defensive of my fairly new gaming laptop...

Im using Feisty, but htop works well... I cant copy though.. so I dont think its going to do much help with this post..

Once again Java is taking 92 to 100% of my CPU...

Revision: Java version is 1.5.0.. I think thats even what frostwire suggested. I think sun java has the 5.0 runtime environment, but Id almost be afraid to try an ENVIRONMENT if the PLUGIN demands so much...

---

### Post by STREETURCHINE on 2007-03-31
ok so run frostwire and stuf and test again but i think the results will be the same,i would say java is your problem ,i will do a search and find out how to kill it

---

### Post by GSF1200S on 2007-03-31
> **STREETURCHINE said:**
> ok so run frostwire and stuf and test again but i think the results will be the same,i would say java is your problem ,i will do a search and find out how to kill it

Kill the high usage or kill the process? If java is killed, frostwire wont run...

---

### Post by STREETURCHINE on 2007-03-31
how did you install frostwire,?

it may pay to uninstall frostwire and reinstall it again from here

[http://www.ubuntuforums.org/showthread.php?t=305337&highlight=frostwire](http://www.ubuntuforums.org/showthread.php?t=305337&highlight=frostwire)

it is the one i installed and it seems fine

---

### Post by GSF1200S on 2007-03-31
> **STREETURCHINE said:**
> how did you install frostwire,?

it may pay to uninstall frostwire and reinstall it again from here

[http://www.ubuntuforums.org/showthread.php?t=305337&highlight=frostwire](http://www.ubuntuforums.org/showthread.php?t=305337&highlight=frostwire)

it is the one i installed and it seems fine

For one, how do I uninstall java? Ill have to find that out. Regaurdless, the terminal keeps give me a 404 not found when I do the wget code... hmm...

---

### Post by STREETURCHINE on 2007-03-31
try 

```
sudo aptitude uninstall frostwire
```



```
sudo rm -r /user/bin/java
```

---

### Post by revilodraw on 2007-05-01
i have a core 2 duo laptop and when i run frostwire, one core runs at 100% the whole time and cpu temp runs at about 52  degrees... turn frostwire off and both cpu's run in the single figures, and the temperature drops 10 degrees...i cant believe it could be **that** cpu intensive...

---

### Post by mahiyar on 2007-05-01
I too have frostwire installed but have never had such problems, though java eats quiet a bit of processing power. Try this to select a different version of java >> sudo update-alternatives --config java. BTW I installed all the java related programmes from add remove and then used this command to select version above 1.4

---

