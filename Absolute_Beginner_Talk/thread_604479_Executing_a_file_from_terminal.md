---
title: "Executing a file from terminal"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by thelugnut on 2007-11-06
As a I am really new to Ubuntu and Linux, I decided to follow along with a tutorial which constructs a  html page as the program purpose.

Things were going along very well, until I tried to execute the file from the terminal.

I get the following error message:

> /home/james/bin/page8.html: line 1: syntax error near unexpected token `newline'
/home/james/bin/page8.html: line 1: `  <html>'

If, however I navigate to the file itself, located in my 'bin', and click on the file itself, I get the dialog box, asking if I want to "Run in terminal", "Display", "XCancel" or just "Run".

Selecting "Display" opens my browser and displays the page perfectly.

I have another file in my bin which executes very well from the terminal.

What have I done wrong, or omitted or what?

I include the written file here:

> <html>
  <head>
    <title>System Information for james-desktop</title>
    </head>
  <body>
    <h1>System Information for james-desktop</h1>
    <p>Updated on 11/05/2007 08:39:24 PM IST by james</p>
    <h2>System release info</h2>
<p>Function not yet implemented</p>
    <h2>System uptime</h2>
<pre>
 20:39:24 up 11:43,  3 users,  load average: 0.10, 0.06, 0.01
</pre>
    <h2>Filesystem space</h2>
<pre>
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             62144196   3815928  55171496   7% /
varrun                 1037884       104   1037780   1% /var/run
varlock                1037884         0   1037884   0% /var/lock
procbususb             1037884       136   1037748   1% /proc/bus/usb
udev                   1037884       136   1037748   1% /dev
devshm                 1037884         0   1037884   0% /dev/shm
lrm                    1037884     33788   1004096   4% /lib/modules/2.6.20-16-generic/volatile
</pre>
    <h2>Home directory space by user</h2>
<pre>
Bytes Directory
48208	/home/james
</pre>
  </body>
</html>

Thank you

---

### Post by kevinatkins on 2007-11-06
Hi,

OK, an HTML file isn't actually an executable file - it's simply a set of markup instructions which your web browser uses to render the web page.

If, however, you want to invoke your web browser to display the page, you'd simply enter -

firefox pagename.html

from the command line

hope i've understood your question correctly

---

### Post by mali2297 on 2007-11-06
> **thelugnut said:**
> As a I am really new to Ubuntu and Linux, I decided to follow along with a tutorial which constructs a  html page as the program purpose.

Things were going along very well, until I tried to execute the file from the terminal.

I get the following error message:



If, however I navigate to the file itself, located in my 'bin', and click on the file itself, I get the dialog box, asking if I want to "Run in terminal", "Display", "XCancel" or just "Run".

Selecting "Display" opens my browser and displays the page perfectly.

I have another file in my bin which executes very well from the terminal.

What have I done wrong, or omitted or what?

I include the written file here:



Thank you

Is it this tutorial?
[http://www.linuxcommand.org/wss0030.php](http://www.linuxcommand.org/wss0030.php)

In that case, it seems that you already have run the program to produce an html file. The file was created when you typed something similar to
```

make_page > page8.html

```

If you want to view the result without leaving the terminal, you can use
```

w3m /home/james/bin/page8.html

```
(Press q to quit w3m.)

---

### Post by nhandler on 2007-11-06
You can also use
```
lynx w3m /home/james/bin/page8.html
```
That will allow you to view the page in the terminal similar to w3m.

If you want to view the html code in the terminal, type
```
cat w3m /home/james/bin/page8.html
```

If you want to edit the html code in the terminal, type
```
nano w3m /home/james/bin/page8.html
```
or
```
pico w3m /home/james/bin/page8.html
```
or
```
vim w3m /home/james/bin/page8.html
```

---

### Post by thelugnut on 2007-11-06
Thanks for the replies to everyone.

Slowly, ever so slowly I am beginning to see a teeny tiny light at the end of the tunnel.

](*,)

---

