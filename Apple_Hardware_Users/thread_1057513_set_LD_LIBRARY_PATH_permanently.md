---
title: "set LD_LIBRARY_PATH permanently"
date: 2009-02-01
forum: Apple Hardware Users
---

### Post by ecinar on 2009-02-01
Hello all,

I need to set LD_LIBRARY_PATH so that all applications can use this updated path. 

From the command line I use export LD_LIBRARY_PATH=/usr/local/Aria/lib and later run a command sudo ldconfig 

but this doesn't work for my java Eclipse compiler to use it. and everytime I open a command line I have to enter these commands.

I modified /etc/ld.conf file and put /usr/local/Aria/lib  line at the end of the file but it didn't work although I run ldconfig command or restart the system. 

I appreciate any help of yours

Thanks in advance

---

### Post by hyperboloid on 2009-02-02
Are you using the bash shell? (The default.) 

If so, I think you would add a line to the .bashrc file in your home directory. Just open it with an editor, gedit will do fine, and add the lines

LD_LIBRARY_PATH=/usr/local/Aria/lib
export LD_LIBRARY_PATH

to the end of the file, and save. You will need to start a new terminal session in order for the changes to take effect, or logout and login again. 

Please let us know if it works.

---

### Post by cyberdork33 on 2009-02-02
> **hyperboloid said:**
> if so, i think you would add a line to the .bashrc file in your home directory. Just open it with an editor, gedit will do fine, and add the lines

ld_library_path=/usr/local/aria/lib
export ld_library_path

to the end of the file, and save. You will need to start a new terminal session in order for the changes to take effect, or logout and login again. 
+1

---

### Post by ecinar on 2009-02-02
> **hyperboloid said:**
> Are you using the bash shell? (The default.) 

If so, I think you would add a line to the .bashrc file in your home directory. Just open it with an editor, gedit will do fine, and add the lines

LD_LIBRARY_PATH=/usr/local/Aria/lib
export LD_LIBRARY_PATH

to the end of the file, and save. You will need to start a new terminal session in order for the changes to take effect, or logout and login again. 

Please let us know if it works.

Thanks a lot! that worked for me ! ;)

---

