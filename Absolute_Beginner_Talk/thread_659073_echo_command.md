---
title: "echo command"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by linux44 on 2008-01-05
hi
i use echo in terminal to create text file i.e:
echo 133 >abcd.txt 
and that wirte all the information in first line how about if i want to use 2 line like :
write 133 in first line and 123 in secound line 
any idea?
thanks

---

### Post by master_kernel on 2008-01-05
> **linux44 said:**
> hi
i use echo in terminal to create text file i.e:
echo 133 >abcd.txt 
and that wirte all the information in first line how about if i want to use 2 line like :
write 133 in first line and 123 in secound line 
any idea?
thanks
Use the -e command to enable backslash commands and use \n to make a new line. For example:
```
echo -e "133\n123" > abcd.txt
```
Outputs:
```
$ cat abcd.txt 
133
123
```

---

### Post by aktiwers on 2008-01-05
```
echo -e "133 \n 123" >abcd.txt
```

Check also:
```
man echo
```

---

### Post by The Cog on 2008-01-05
Also possibly:
```
echo 133 > abcd.txt
echo 123 >> abcd.txt
```

---

