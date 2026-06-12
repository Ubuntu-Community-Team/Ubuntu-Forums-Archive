---
title: "how to add new path into $PATH  variable of current shell by executing a file or scri"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by mokkai on 2007-12-26
how to add new path into $PATH  variable of current shell by executing a file or script

---

### Post by meindian523 on 2007-12-26
In terminal
```

echo %PATH='your new path (make sure to include all directories you want in your path separated by spaces)'
```

Remember to use the single quotes...   ```
'
```

---

### Post by mokkai on 2007-12-26
echo %PATH='/home/username/mybin:$PATH'

my current shell $PATH is not changed

any other ?

---

### Post by taurus on 2007-12-26
You can edit your ~/.bashrc and add these two lines.

```
PATH=$PATH:new_path:more_new_path
export PATH
```
Save it and then run

```
source ~/.bashrc
```

---

### Post by mokkai on 2007-12-26
> **taurus said:**
> You can edit your ~/.bashrc and add these two lines.

```
PATH=$PATH:new_path:more_new_path
export PATH
```
Save it and then run

```
source ~/.bashrc
```

actually i have two same package with diffrent version

so dynamically i want to add 

export PATH=/home/username/package1/bin:$PATH
or
export PATH=/home/username/package2/bin:$PATH
 
like above 
so ~/.bashrc is not satisfied me

any other ?

thank you

---

### Post by taurus on 2007-12-26
What do you mean by not satisfied you?  You added the new path and you sourced it, ~/.bashrc, again.

---

### Post by mokkai on 2007-12-26
> **taurus said:**
> What do you mean by not satisfied you?  You added the new path and you sourced it, ~/.bashrc, again.

i am explain what is my problem
i have 3 version of ruby on rails(ror)

/home/username/ror1/bin
/home/username/ror2/bin
/home/username/ror3/bin

suppose  if i want to create a project in ror1 

then i should type export PATH=/home/username/ror1/bin:$PATH
like wise for other 2 or 3

so every time i should type this "export PATH=/home/username/ror1/bin:$PATH" in every terminal 

for that i want to keep it in a script 
like 

v1 --->export PATH=/home/username/ror1/bin:$PATH
v2 --->export PATH=/home/username/ror2/bin:$PATH
v3 --->export PATH=/home/username/ror3/bin:$PATH

so i can simply type v2 to get my ror2 environment

like this

---

### Post by taurus on 2007-12-26
```
gedit v1
```
And add these lines to it.

```

#!/bin/bash
export PATH=/home/**username**/ror1/bin:$PATH

```
Save it.  Then, change permissions and execute it.

```
chmod 755 v1
./v1
```
 
Make sure you change **username** to your actual log in name _unless_ you use username as your login name!

Repeat the process for v2 and v3.

---

### Post by The Cog on 2007-12-26
So create a file called v2 with the following contents:
> #!/bin/sh
export PATH=/home/username/ror2/bin:$PATH
ror
and make it executaboe with the command:
chmod +x v2
but you will have to launch it with ./v2 unless you put in somewhere on your current path.

You could also create a launcher icon with the command line:
**export 'PATH=/home/username/ror3/bin:$PATH' ; ror**

or create an alias for v2 to the command:
**export 'PATH=/home/username/ror3/bin:$PATH' ; ror**
in your ~/.bashrc

---

### Post by jonmartin on 2007-12-26
> **The Cog said:**
> So create a file called v2 with the following contents:

and make it executaboe with the command:
chmod +x v2
but you will have to launch it with ./v2 unless you put in somewhere on your current path.

You could also create a launcher icon with the command line:
**export 'PATH=/home/username/ror3/bin:$PATH' ; ror**

or create an alias for v2 to the command:
**export 'PATH=/home/username/ror3/bin:$PATH' ; ror**
in your ~/.bashrc

The script is correct, but you must launch it like this

$ . ./v2

Just executing as a normal script doesn't do the trick. Also I cannot see how making a desktop launcher for such a script could have any function at all.

---

### Post by mokkai on 2007-12-26
> **jonmartin said:**
> The script is correct, but you must launch it like this

$ . ./v2

Just executing as a normal script doesn't do the trick. Also I cannot see how making a desktop launcher for such a script could have any function at all.

woooowww....perfect answer..thank you jonmartin...

thank you very much to all of you ....

by 
   mokkai

---

### Post by anubhavrocks on 2007-12-26
Modify the script as per your requirements

```
#!/bin/bash
BASEPATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
PATH1=/home/username/ror1/bin
PATH2=/home/username/ror2/bin

if [ $# != 1 ]
  then
  echo "Wrong Arguments"
  exit
fi

if [ $1 -eq 1 ]
  then 
  export PATH=$PATH1:$BASEPATH
elif [ $1 -eq 2 ]
  then
  export PATH=$PATH2:$BASEPATH
fi
```

Name this script as maybe setpath.sh
chmod +x setpath.sh

If you give 1 as argument it will set the path to PATH1 and so on

This is how you would use it
anubhav@igloo:~$ source ./setpath.sh 2

This command will set the path to PATH2 
Remember that you use it with the "source" command

---

### Post by meindian523 on 2007-12-26
> **meindian523 said:**
> In terminal
```

echo %PATH='your new path (make sure to include all directories you want in your path separated by spaces)'
```

Remember to use the single quotes...   ```
'
```

oops,I meant echo $PATH

---

### Post by The Cog on 2007-12-26
> **jonmartin said:**
> The script is correct, but you must launch it like this
$ . ./v2

Just executing as a normal script doesn't do the trick. 

Yes it does. After setting the executable flag with chmod, you can launch it directly with **./v2**
> 
Also I cannot see how making a desktop launcher for such a script could have any function at all.
You are right - that doesn't work.

---

### Post by mokkai on 2007-12-26
> **anubhavrocks said:**
> Modify the script as per your requirements

```
#!/bin/bash
BASEPATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
PATH1=/home/username/ror1/bin
PATH2=/home/username/ror2/bin

if [ $# != 1 ]
  then
  echo "Wrong Arguments"
  exit
fi

if [ $1 -eq 1 ]
  then 
  export PATH=$PATH1:$BASEPATH
elif [ $1 -eq 2 ]
  then
  export PATH=$PATH2:$BASEPATH
fi
```

Name this script as maybe setpath.sh
chmod +x setpath.sh

If you give 1 as argument it will set the path to PATH1 and so on

This is how you would use it
anubhav@igloo:~$ source ./setpath.sh 2

This command will set the path to PATH2 
Remember that you use it with the "source" command


thank you

---

