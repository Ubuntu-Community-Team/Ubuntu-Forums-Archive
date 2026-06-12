---
title: "[SOLVED] Executing files by icon clicking."
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Glich on 2007-08-30
Hi, I can execute python programs in the terminal:

glich@Glich:~/Desktop/Docs/Python/Maths$ ./mathsProblem.py
[6, 3, 10, 5, 16, 8, 4, 2, 1]
Number of numbers: 9
glich@Glich:~/Desktop/Docs/Python/Maths$ 

but how can I execute the python files by double clicking on their file icons?

Also, I have downloaded uDraw ([http://www.informatik.uni-bremen.de/uDrawGraph/en/uDrawGraph/uDrawGraph.html](http://www.informatik.uni-bremen.de/uDrawGraph/en/uDrawGraph/uDrawGraph.html)) as an executable and am able to execute it from a file browser launched under root by clicking on the file icon. But, how do I launch it under my user by clicking on the icon? I am alredy abled to do this by using the terminal.

Thanks.

---

### Post by Majorix on 2007-08-30
About the first question, right click the file, select properties, then click the open with tab. From there select manual and type in python when you get a textbox. Then whenever you click that file it will open with Python.

BUT!

You won't get to see the end of the program flow I think, as when you do what I described above, the program will automatically close itself when the i/o session is over. So I would just stick with the terminal if I were you.

---

### Post by annda on 2007-08-30
> **Majorix said:**
> You won't get to see the end of the program flow I think, as when you do what I described above, the program will automatically close itself when the i/o session is over. So I would just stick with the terminal if I were you.

or you can create a launcher on your Desktop (right mouseclick) with the command you use in the terminal (adjust the path, because the script will be in a different directory) and check the option 'execute in terminal'.

as to not being able to run uDraw as a regular user, check the file's permissions and make sure it is readable and executable by 'others' (run the file manager as root, right-click the file and check the right permissions). then create another launcher.

---

### Post by Glich on 2007-08-30
Thanks for your answer. Is it possible to start the terminal and make that terminal open the python file when I click on it?

---

### Post by annda on 2007-08-30
i'm sorry, i've just tested a python script and the window closes just after executing, so it' s not much use for you. but it should work with uDraw i think.

---

### Post by Glich on 2007-08-30
Thanks for your persistence. I am going to search for software like uDraw but which is closer to python. I only wish I had the knowledge and experience to answer other questions in this forum, when I have that I will. Thanks again.

---

