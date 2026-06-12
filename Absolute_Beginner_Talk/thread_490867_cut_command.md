---
title: "cut command"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by niko7865 on 2007-07-02
running 'sensors' outputs this code
> k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +39°C
Core1 Temp:
             +40°C

....

I'm trying to use a combination of grep and cut to copy just the two temperatures separately but it's not working since they are on different lines.

If it 'sensors' displayed
> k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp: +39°C
Core1 Temp: +40°C

....

Then I could just use
> sensors | grep "Core0" | cut -d" " -f3
sensors | grep "Core1" | cut -d" " -f3
But, unfortunately that isn't the case.

So does anyone know how to do it when they are on separate lines?

---

### Post by Ocxic on 2007-07-03
"-d" " -f3"

i think this is the part of your command that it causing you problems, "-d" " -f3" is not a commnad, I'm not sure what your trying to do, and I'm sorry i can't offer any more help.

---

### Post by niko7865 on 2007-07-03
woops, I meant 'cut -d" " -f3', edited to fix mistake. I'm just trying to cut the two core temps seperatly so I can display them in conky.

---

### Post by pbaumgar on 2007-07-03
Try this:

sensors | grep 'Core' | cut -d: -f2

or use awk:

sensors | grep 'Core' | awk '{print $3}'

With the cut command '-d' needs a delimeter.  In this case it is the colon.

---

### Post by niko7865 on 2007-07-03
Well I figured out what my real problem is, grep is only returning the line with the search pattern (should have known that), I need grep to return the line AFTER the line containing the pattern it's searching for...somehow.

---

### Post by pbaumgar on 2007-07-03
Have a look at the grep man page.  

grep -A 1 <pattern> 

should do the trick.

---

### Post by niko7865 on 2007-07-03
Ya, I found that out just after posting, things are easier when you actually know what's wrong :p 

But now I've got a new problem
> sensors | grep -A 1 'Core0' | cut -c15-19

outputs a new line and the the temperature, and I can't seem to get rid of the new line

---

### Post by pbaumgar on 2007-07-03
Well.. I'm sure there is a better way, but you could use sed on the end to strip the blank lines...

grep -A1 <pattern> | cut <stuff to cut> | sed '/^$/d'

---

### Post by niko7865 on 2007-07-03
That worked great, thanks!

---

