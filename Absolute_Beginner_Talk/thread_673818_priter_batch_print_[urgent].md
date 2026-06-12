---
title: "priter batch print [urgent]"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by afeasfaerw23231233 on 2008-01-21
how to make printer batch print 100 different jpeg images without any modification?
i can do that in win xp with the hp driver utility. my printer model is hp deskjet 2360

edit: i also have a bunch of pdf files [100+] to print, how can i print them all without opening every file?

---

### Post by ikex on 2008-01-21
for the pdf files, if there in the same folder
do it from the command line as such

```

lpr -p <printer name> -o <print options if wanted> /location/to/folder**/***

```

to figure out what options your printer is capable of:

```

lpoptions -p <printer name> -l

```

---

### Post by afeasfaerw23231233 on 2008-01-22
where to know my <printer name>?
lpoptions -p <Deskjet_D2300_series> -l   doesn't work

---

### Post by clwhitt on 2008-02-04
You can identify your printer with the following command:
[COLOR="Blue"]lpstat -p -d[/COLOR]

You can use the lpr command without specifying your printer if the printer you want is the default.

[COLOR="Blue"]lpr /your_path/your_filename[/COLOR] will print to your default printer. Use wildcards  or multiple names to get it to print a batch job

Chuck

---

