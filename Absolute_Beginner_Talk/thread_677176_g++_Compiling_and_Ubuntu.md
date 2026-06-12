---
title: "g++ Compiling and Ubuntu"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by mcfunk on 2008-01-24
Hello, 

     I installed ubuntu on my Dell inspiron 8600 which is great because the wireless support for it was automatic! I have a problem with the g++ complier I compiled a little program which works no problem on a different bash shell I used (the one we use for class) but after I compile it on my new ubuntu install I am not able to run the a.out...it just gives me an error. Everything compiled correctly but I am not sure what to do. Can you advise? Thanks in advance!

---

### Post by taurus on 2008-01-24
Have you installed the build-essential package first before you compiled your program?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install build-essential
```

And if you have installed it, then what is the exact error when you run it?

---

### Post by stchman on 2008-01-24
> **mcfunk said:**
> Hello, 

     I installed ubuntu on my Dell inspiron 8600 which is great because the wireless support for it was automatic! I have a problem with the g++ complier I compiled a little program which works no problem on a different bash shell I used (the one we use for class) but after I compile it on my new ubuntu install I am not able to run the a.out...it just gives me an error. Everything compiled correctly but I am not sure what to do. Can you advise? Thanks in advance!

Since you can compile the program then build-essential is installed.  I believe for Gutsy build-essential is installed by default.

This is pretty trivial but you need to include the path when running the program.  Type this:

```
./a.out
```

Notice the ./ that is the path.  This assumes your terminal is open in the directory of the a.out program.

---

### Post by erginemr on 2008-01-24
Also do not forget to give your new program correct permissions to execute:
```
chmod u+x program_name
```

---

