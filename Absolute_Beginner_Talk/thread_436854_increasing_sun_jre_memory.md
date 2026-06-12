---
title: "increasing sun jre memory"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2007-05-08
I trying to use Electric VLSI Design system on kubuntu. It is written in java and require jre 1.5 or higher. I have installed JRE 1.5 from sun microsystems .When i use java -jar electric .jar ,it  sys that your curren memory is 66MEG and Electric requires 1000MEG. plz increase the memory . On same computer using windows as well as freespire Linux i can run it without any error. 
plz tell me how to get out of it

---

### Post by Seine on 2007-05-08
Type the following to see some VM options
```
java -X
```

You can probably get the effect you need by setting the max heap size with:
```
java -Xmx1024m -jar electric.jar
```

See how you go.

---

### Post by u04f061 on 2007-05-08
thanks. it gave me this warning

GNU Release can't find the Bean Shell: bsh.Interpreter

due to this ,it is not working properly.plz tell me what to do?

---

