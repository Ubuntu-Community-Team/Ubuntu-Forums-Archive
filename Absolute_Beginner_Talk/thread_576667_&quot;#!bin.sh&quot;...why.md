---
title: "&quot;#!/bin.sh&quot;...why?"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by philip.yhelzon on 2007-10-15
I've started learning shell programing...:confused:
In the book I'm reading it says that I should start every script with: "#!/bin/sh"
I tried doing as the book says but every time the script have some simple math in it, the script just dosn't work. 
But if i take "#!/bin/sh" out of the scrip, suddenly the script starts working just fine. ](*,)](*,)](*,)

for E.G:
#the script counts the number is *.sh files in the folder
n=0
p=1
for i in *.sh ; do
  n=$p
  echo "found a script:" $i
  p=$[n+1]
done 
echo "the numbet of scripts in this filder is:" $n

If I add "#!/bin/sh" it stops working.....why??????

---

### Post by Tomosaur on 2007-10-15
/bin/sh is just a link to your default shell (in Ubuntu the default shell is Dash) - so if your shell doesn't support the syntax in the book - which probably doesn't use Dash, by the way - then you will receive errors.

Find out what shell the book is written for, then find out the equivalent syntax for Dash. Alternatively, install the correct shell, then use a direct hash-bang. Let's say the shell you need is KSH - you'd use the following:
```

#!/bin/ksh

```

That line tells your system which program to use to read the script.

---

### Post by maybeway36 on 2007-10-15
I suppose most of those scripts are for Bash, so:
```
#!/bin/bash
```
The reason Ubuntu uses dash as /bin/sh is to make scripts faster.

---

### Post by philip.yhelzon on 2007-10-16
The book is named:LINUX:
Rute User's Tutorial and Exposition
(Version 1.0.0)
And as i understand its for Debian (so there should be no problems with Ubuntu).
If all of the scripts work fine without telling them where to find she shell, then maybe the system dos it automatically?

Are there lots of shell versions with different syntax each?   aren't they all Unix based and should work the same?

How do I know which shell is active on my PC?

---

