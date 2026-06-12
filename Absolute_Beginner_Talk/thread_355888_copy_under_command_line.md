---
title: "copy under command line"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by Jun0 on 2007-02-07
Hi Ev8d,
If I would like all txt-type files(*.txt) under a specific partition to be copied into a specific directory(e.g. mnt/a/txt),how could it be done?
It's very simple under Windows series desktop.
But if I am under Unix/linux COMMAND LINE(without x-desktop)?

---

### Post by etank on 2007-02-07
Assuming that everything is mounted (CD, Floppy, whatever) then```
cp *.txt /dest/dir
```that will copy all .txt files to the destination dir assuming you are in the dir with the .txt files.

---

### Post by Jun0 on 2007-02-07
> **etank said:**
> Assuming that everything is mounted (CD, Floppy, whatever) then```
cp *.txt /dest/dir
```that will copy all .txt files to the destination dir assuming you are in the dir with the .txt files.

but I need all the files in that [color=red]PARTITON!!![/color]
it may possess many sub-directory, i mean.
maybe your code is for [color=red]CURRENT[/color] directory only?

---

### Post by Maestro23 on 2007-02-07
> **Jun0 said:**
> but I need all the files in that [color=red]PARTITON!!![/color]
it may possess many sub-directory, i mean.
maybe your code is for [color=red]CURRENT[/color] directory only?

Type the following in a terminal:

#man cp

Will give you the syntax for the cp command with all arguments or this link: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

Sounds like you need the recursive argument for directories.

---

### Post by Moldz on 2007-02-07
Also, you could use the 'find' program with the -exec option.  Double check the syntax, but it would be something like this:

```
find /home/blah -name *.txt -exec cp {} /mnt/txt/ \;
```

---

### Post by Jun0 on 2007-02-07
> **Moldz said:**
> Also, you could use the 'find' program with the -exec option.  Double check the syntax, but it would be something like this:

```
find /home/blah -name *.txt -exec cp {} /mnt/txt/ \;
```

this seems to be very close to what i want

is this way workable for [color=red]mv[/color] also?
if i wanna move files not copy them?

---

### Post by Jun0 on 2007-02-07
> 
 [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

well?
what is this link for?
i dont get it
> 
Sounds like you need the recursive argument for directories.

recursive arument?
can you explain more?

---

### Post by Maestro23 on 2007-02-07
> **Jun0 said:**
> well?
what is this link for?
i dont get it


recursive arument?
can you explain more?


In your first post, you wanted to know how to use the copy command, that page shows you.

Shows you the syntax(structure) for using the [COLOR="Red"]cp (copy)[/COLOR]command in a terminal.  Also it shows you how to use the arguments(additional commands) for[COLOR="Red"] cp[/COLOR] to accomplish different things.  This is the same kind of info you will see when you look at a [COLOR="Red"]"man"[/COLOR] page for a command.

---

