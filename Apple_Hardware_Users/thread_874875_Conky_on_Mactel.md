---
title: "Conky on Mactel"
date: 2008-07-30
forum: Apple Hardware Users
---

### Post by Kooothor on 2008-07-30
Hi folks, so I start this thread for conky users on Mactel.

Under Hardy Heron, I've setup applesmc and now I can get this kind of output :
kooothor@ktr-linux:~$ sensors
applesmc-isa-0300
Adapter: ISA adapter
fan1:       3991 RPM
ERROR: Can't get value of subfeature temp2_input: I/O error
temp2:        +0.0°C                                    
temp4:       +52.5°C                                    
ERROR: Can't get value of subfeature temp7_input: I/O error
temp7:        +0.0°C                                    
temp9:       +47.8°C  

So, as you can see, I have some I/O errors that I can't manage to make disappear (and it's not always the same sensors that give me errors)
but let's not talk about that (remember the thread topic ?)

Let's tallk about how I can put this output (or some of it) into my conky :)

Cheers

---

### Post by cyberdork33 on 2008-07-30
> **Kooothor said:**
> Hi folks, so I start this thread for conky users on Mactel.

Under Hardy Heron, I've setup applesmc and now I can get this kind of output :
kooothor@ktr-linux:~$ sensors
applesmc-isa-0300
Adapter: ISA adapter
fan1:       3991 RPM
ERROR: Can't get value of subfeature temp2_input: I/O error
temp2:        +0.0°C                                    
temp4:       +52.5°C                                    
ERROR: Can't get value of subfeature temp7_input: I/O error
temp7:        +0.0°C                                    
temp9:       +47.8°C  

So, as you can see, I have some I/O errors that I can't manage to make disappear (and it's not always the same sensors that give me errors)
but let's not talk about that (remember the thread topic ?)

Let's tallk about how I can put this output (or some of it) into my conky :)

Cheers
That's actually really good output... What machine / version are you on?

P.S. can you add a "conky" tag to this thread? I can only put two.

---

### Post by Kooothor on 2008-07-30
@cyberdork33 :: I can't manage to add tags :(
I'm running a MacBook black with 4Go RAM, latest generation :)

---

### Post by easybake on 2008-07-30
You are going to want to use a execi with a grep something like this for each of the sensors you want in conky. ```
${execi sensors | grep -A 1 &#8216;NAME OF WHATEVER&#8242; | cut -c13-16 | sed &#8216;/^$/d&#8217;} C
```

That may be wrong because I can't check it now.

---

### Post by Kooothor on 2008-07-31
> **easybake said:**
> You are going to want to use a execi with a grep something like this for each of the sensors you want in conky. ```
${execi sensors | grep -A 1 ‘NAME OF WHATEVER&#8242; | cut -c13-16 | sed ‘/^$/d’} C
```

That may be wrong because I can't check it now.

I've just tried with 

```
${execi sensors | grep -A 1 'fan1'}
```

(coz I don't know what for is the rest of the things you wrote oO)


But conky only shows me $execi
nothing more, like it doesn't know what it is !

Thanks for trying though :)

---

### Post by easybake on 2008-07-31
> **Kooothor said:**
> I've just tried with 

```
${execi sensors | grep -A 1 'fan1'}
```

(coz I don't know what for is the rest of the things you wrote oO)


But conky only shows me $execi
nothing more, like it doesn't know what it is !

Thanks for trying though :)

I pulled that one from somewhere, this one actually will work though sorry
```
${exec sensors | grep  "Core0 Temp" | cut -c13-16}
```


EDIT: dont use 'execi' use 'exec'. I'm retarded.

---

### Post by Kooothor on 2008-07-31
> **easybake said:**
> I pulled that one from somewhere, this one actually will work though sorry
```
${exec sensors | grep  "Core0 Temp" | cut -c13-16}
```


Hey, it works ! :D (well, I just do ${exec sensors}, the grep on Core0 Temp doesn't work.
But there is too many I/O errors, so it works one time on three maybe...

I DO have to get rid of these I/O errors !!!

But thanks for the "exec", that was the thing I missed :)

edit : I've added ```
{color grey}Fan Speed:
${exec sensors | grep 'fan1'}

```
and it's great :D

---

### Post by cyberdork33 on 2008-07-31
you have to use coretemp to read the CPU temperatures. make sure it is loaded.

Maybe you could write a small tutorial on how you got everything working. I am sure that it would be helpful to people. Maybe add a section to the Macbook wiki:
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

---

### Post by Kooothor on 2008-09-04
> **cyberdork33 said:**
> you have to use coretemp to read the CPU temperatures. make sure it is loaded.


Cyberdork, did you manage to load coretemp ?

I get this :
```
$ sudo modprobe -v coretemp
insmod /lib/modules/2.6.24-19-generic/kernel/drivers/hwmon/coretemp.ko 
FATAL: Error inserting coretemp (/lib/modules/2.6.24-19-generic/kernel/drivers/hwmon/coretemp.ko): No such device

```

and in logs :

```
 cat /var/log/messages | grep coretemp
Sep  4 17:56:21 ktr-linux kernel: [ 5590.947772] coretemp: Unknown CPU model 17

```

And in Googling, I find lot of guys having this problem but no solutions :(

I'm running Ubuntu 8.04 with kernel 2.6.24-19-generic on x86-64

---

### Post by Kooothor on 2008-09-04
Anyway, I've managed to fiddle around the I/O errors I get from the command "sensors".

Here is a pic of my conky :

[IMG]http://xs331.xs.to/xs331/08364/screenshot7596.png[/IMG]

And here is my conky.conf :

```
TEXT
${color orange}$nodename - $sysname $kernel on $machine
$hr
${color orange}MONITORING ${hr 2}$color
${color grey}Uptime:$color $uptime
${color grey}Frequency (in MHz):$color $freq
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color grey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color grey}CPU Usage:$color $cpu% ${cpubar 4}
${color orange}TEMPERATURE  ${hr 2}$color
${exec sensors | grep '+4' | cut -c1-16}
${color grey}${exec sensors | grep 'RPM'}
${color orange}File systems ${hr 2}$color
 / $color${fs_free /}/${fs_size /} ${fs_bar 6 /}
${color orange}NETWORK ${hr 2}$color
Up:$color ${upspeed eth0} k/s${color grey} - Down:$color ${downspeed eth0} k/s
${color orange}KOIKITOURNE ${hr 2}$color
${color grey}Processes:$color $processes  ${color grey}Running:$color $running_processes
${color grey}Name                  PID   CPU%   MEM%
${color #FFFFFF} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color #CCCCCC} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color #999999} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color #666666} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}
```

So the interesting part is :

${exec sensors | grep '+4' | cut -c1-16}
I've done grep +4 to avoid getting the lines with the I/O error
and the cut -c1-16 is for avoiding the ° character wich doesn't pass :(

${color grey}${exec sensors | grep 'RPM'}
and this is because sometimes I get fan1: XXXXRPM
and sometimes Exhaust : XXXXRPM
so I grepped RPM :)

ENJOY !

---

### Post by cyberdork33 on 2008-09-04
> **Kooothor said:**
> Cyberdork, did you manage to load coretemp ?
I did at one time, but not recently. I don't monitor my temps like that because I am not concerned with them really. (on an iMac). I had to install some packages, then run the sensors detect thing, and then I could read the coretemp output. Sorry I can't really help more, it was awhile ago, and I don't even have the links anymore that I used.

---

### Post by Kooothor on 2008-09-05
ok cyberdork.


--

This is a more general question on conky :
How do I make arithmetic operation on a number.
See, I can probe my unseen messages but I don't know why, it starts with 1904, not 0. So what I want to do is just do 'the result of unseen mails minus 1904'.

Can someone help me on this ?

My line is 
```
${color red}${pop3_unseen pop.server.fr login pass} mails
```

I guess I have to pipe something after, nope ?

thx :)

---

### Post by cyberdork33 on 2008-09-05
> **Kooothor said:**
> ok cyberdork.


--

This is a more general question on conky :
How do I make arithmetic operation on a number.
See, I can probe my unseen messages but I don't know why, it starts with 1904, not 0. So what I want to do is just do 'the result of unseen mails minus 1904'.

Can someone help me on this ?

My line is 
```
${color red}${pop3_unseen pop.server.fr login pass} mails
```

I guess I have to pipe something after, nope ?

thx :)
I am no good with bash, but I think you need to format your bash command that shows what you want on the cli, then have to do an execi with that bash command in it in order to display in conky. If you don't want your conkyrc getting messy, you can create a shell script that does whatever, then just run the script from your conkyrc.

You might get better help on this elsewhere since it is really not dependent on you having a Mac. I am sure someone out there has encountered this problem before, and there is likely already a solution.

---

### Post by Kooothor on 2008-09-05
Yeah , you're right. But nvmd anyway, the whole pop system is shitty.
Everytime I get a new messages, it adds up and that's it, don't care if it's read or not...

---

### Post by cyberdork33 on 2008-09-05
> **Kooothor said:**
> Yeah , you're right. But nvmd anyway, the whole pop system is shitty.
Everytime I get a new messages, it adds up and that's it, don't care if it's read or not...

I was wondering how that would work.

---

