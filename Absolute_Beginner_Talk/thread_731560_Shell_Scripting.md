---
title: "Shell Scripting"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by Doctor Debian on 2008-03-22
Hi  everyone,

Looking for a way to set the value of a variable in a terminal, e.g it asks the user: Would you like to install blehblehbleh? y/n, then it sets the variable in the code to that value.

Thanks!
DOC DEB

---

### Post by Hospadar on 2008-03-22
are you asking how you code input into shell scripts?

If so, just do it exactly like you'd type it.  For example, an installation might look like ```
#!/bin/bash

sudo apt-get install <yourpackages>
y

#make sure a newline follows the input, since you'd have to press enter.
```

---

### Post by Doctor Debian on 2008-03-22
Bad example of mine :(

I meant to set the value of a variable inside the script. I plan to ask something like: "Do you have a laptop?" , and use the output later on.

Thanks,
Doc Deb

---

### Post by ad_267 on 2008-03-22
Have a look here: [http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_08_02.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_08_02.html)

```

                #!/bin/bash
                echo Please, enter your name
                read NAME
                echo "Hi $NAME!"
```

---

### Post by ad_267 on 2008-03-22
You can also use arguments when you execute the script from the command line to set variables which is often a more elegant solution.
[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_02.html#AEN4285](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_02.html#AEN4285)

---

