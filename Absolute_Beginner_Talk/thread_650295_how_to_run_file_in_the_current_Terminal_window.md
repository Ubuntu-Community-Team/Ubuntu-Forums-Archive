---
title: "how to run file in the current Terminal window?"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by mokkai on 2007-12-26
how to run file (Allow executing file as program) in the current Terminal window.

actually i open a file named as "p" and i typed below line into that file.
export PATH=/somethng/


after that i open file properties and checked the check box (Allow executing file as program) in permission tab

when i execute that file then that file is executed 
But my current terminal PATH is not affected..

my current PATH must be change.

any idea?

---

### Post by LaRoza on 2007-12-26
If you have a program not in you $PATH, you have to specify its location. 

For apps that are in the pwd (Present Working Directory), type:

```

./programName

```

The "." means "this directory", ".." means go up one directory and "~" means home.

```

#Go to your home directory
cd ~

#Go up one directory
cd ..

#Runn program in this directory
./program

#Show Present Working Directory
pwd

```

---

### Post by splintercellguy on 2007-12-26
Type ./nameoffile, assuming that the file is indeed marked +x.

---

### Post by dnvikram on 2007-12-26
Let Me rephrase your post just to make sure I understood your problem:

You have a file called ,"p" with that line in it and when you execute that ,it should change your current path to the one in script.

First make sure you are in bash.You can check the shell you are in with the command,"ps"

1)Open the file p
2)Put in the lines below:
PATH=/xyz
export PATH
3)save and exit the file
4)chmod 777 p
5) ./p

What the above script will do is,it will set your PATH variable to /xyz.You check this with the command,"echo $PATH"

But,I wouldnt suggest that as it may screw up your shell settings and you will get lot of command not found errors.So,incase you want to add to the existing Shell PATH ,then replace the,"PATH =/xyz" with the below line:

PATH=/xyz:$PATH:.
export PATH

Now run the file p with execute permissions and do an echo $PATH.Now you should be able to see the /xyz in your current path.

---

### Post by mokkai on 2007-12-26
> **dnvikram said:**
> Let Me rephrase your post just to make sure I understood your problem:

You have a file called ,"p" with that line in it and when you execute that ,it should change your current path to the one in script.

First make sure you are in bash.You can check the shell you are in with the command,"ps"

1)Open the file p
2)Put in the lines below:
PATH=/xyz
export PATH
3)save and exit the file
4)chmod 777 p
5) ./p

What the above script will do is,it will set your PATH variable to /xyz.You check this with the command,"echo $PATH"

But,I wouldnt suggest that as it may screw up your shell settings and you will get lot of command not found errors.So,incase you want to add to the existing Shell PATH ,then replace the,"PATH =/xyz" with the below line:

PATH=/xyz:$PATH:.
export PATH

Now run the file p with execute permissions and do an echo $PATH.Now you should be able to see the /xyz in your current path.

i did same as what you told

but my current $PATH is not changed

---

