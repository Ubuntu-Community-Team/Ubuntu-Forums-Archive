---
title: "installing multiple versions of the same program"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by JohnJSal on 2006-08-07
Hi everyone. Quick question about how this works. Vim is already installed by default, but I noticed that there is another version (in Synaptics) that is customized for Python. If I install this, how do I know which version I'll be invoking when I type 'vim' at the terminal?

Also, how can I control where it gets installed?

Thanks.

---

### Post by arjun.shankar on 2006-08-08
Once you got both packages installed and you give this command:

**$ ls -l /usr/bin/vim**

you will see that it is a link to **/etc/alternatives/vim**

so now:

**$ ls -l /etc/alternatives/vim**

ah! It is another link that points to **/usr/bin/vim.python**

So by default, you get the python version when you type **$ vim**

If you want to run the C version:

**$ /usr/bin/vim.basic**

As to controlling the install path, AFAIK, no you can't do it with binary packages. You will have the get the source:

**$ apt-get source vim-python** ;you don't need sudo

then you will have to navigate to the **debian** directory inside the source, and modify the 'rules' file accordingly. Then build the package.

I could be wrong. I'm not really sure if this is how to do it. Any gurus out there?

---

### Post by JohnJSal on 2006-08-08
Thanks very much!

---

### Post by arjun.shankar on 2006-08-08
Always welcome! And besides, I learnt something while trying to answer you.

---

