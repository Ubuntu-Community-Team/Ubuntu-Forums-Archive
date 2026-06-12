---
title: "Ubuntu and a dialup (Lucent) modem"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by teriwood on 2008-04-05
Hi -- very much a beginner, and I'm sure some small step in logic is avoiding me.

I sent my ModemData.txt in, and from that downloaded the current update martian-full-20071011.tar.gz
I've also saved the suggested instruction page found here:
[http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04852.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04852.html)
 
But I've stumped at the first step.  

I have extracted the tar.gz into a folder called martian.  I noted that inside this folder is another called modem.  So I'm assuming that I don't move all the other items in the martian folder into the modem folder.  I'm hoping this is what is meant by creating a directory called martian/modem.  

So leaving it as is on my desktop, I open my terminal and type in the commands on the lnmodem page.

$ cd martian

I've also tried:

cd martian

But in either case it says no such file or directory.  

Please -- what am I doing wrong?

---

### Post by spiderbatdad on 2008-04-05
First cd into Desktop (which is case sensitive)```
cd Desktop/martian
```

---

### Post by zvacet on 2008-04-05
```
cd Desktop
```

---

### Post by teriwood on 2008-04-05
Whoa -- that helped.   However, I'm stalled again.

This time at:

sudo make install

After I punch in the password, it comes up with errors.  Incompatible pointers and various other text -- lots and lots of text.   And I'm at a loss for what to do next.



I should probably point out that I was enough of a newbie, that when I saw this on the instruction page:

[I][COLOR="DarkGreen"]$ ls
ChangeLog  INSTALL  Makefile   modem   scripts
Concept    kmodule  martian.h  README[/COLOR][/I]

I thought all of it was a command.  I cut and pasted all of it.  It took me some time to learn not to put in the "$" each time, and I did not discover that the "ChangeLog  INSTALL  Makefile   modem   scripts
Concept    kmodule  martian.h  README" part was what should show up on the terminal after inputing only "ls" until after I got the answer on how to fix what directory I was using in the terminal.

I'm coming at this from a long way out of understanding.  So hopefully, the answer is obvious to everyone but me.  I hope!

By the way -- the process of figuring this out is not only horrifically terrifying, but damn fascinating when something works out.

Thanks -- very much thanks, for the time you're all spending on this.

---

### Post by bren on 2008-04-05
> After I punch in the password, it comes up with errors. Incompatible pointers and various other text -- lots and lots of text. And I'm at a loss for what to do next.

That sounds a bit wierd
Can you type

$pwd
(this will show your current path or working directory)
and then
$sudo make install
(and post the resulting text)

bren

---

### Post by spiderbatdad on 2008-04-05
Also is there a ./configure step first, as outlined in the readme file? There maybe a number of errors there as a result of lacking the build tools. The build-essential package is usually needed for installing third-party software.```
sudo apt-get install build-essential
```then run through the installation steps again....that is ./configure...make...sudo make install

---

### Post by teriwood on 2008-04-05
Okay, this is what I got:

teriwood@teriwood-desktop:~/Desktop/martain$ pwd
/home/teriwood/Desktop/martain
teriwood@teriwood-desktop:~/Desktop/martain$ 

---

then after "sudo make install" I got the following.  It's not all of it, but it's all that I could get off the terminal.

```

main.c:530: warning: passing argument 2 of â&#8364;&#732;logdebugâ&#8364;&#8482; from incompatible pointer type
main.c:533: warning: implicit declaration of function â&#8364;&#732;printfâ&#8364;&#8482;
main.c:533: warning: incompatible implicit declaration of built-in function â&#8364;&#732;printfâ&#8364;&#8482;
main.c:538: warning: passing argument 1 of â&#8364;&#732;logwarnâ&#8364;&#8482; from incompatible pointer type
main.c:541: warning: incompatible implicit declaration of built-in function â&#8364;&#732;exitâ&#8364;&#8482;
main.c:544: error: â&#8364;&#732;optindâ&#8364;&#8482; undeclared (first use in this function)
main.c:544: warning: comparison between pointer and integer
main.c:545: error: array subscript is not an integer
main.c:545: warning: assignment from incompatible pointer type
main.c:547: warning: comparison between pointer and integer
main.c:548: warning: passing argument 1 of â&#8364;&#732;logwarnâ&#8364;&#8482; from incompatible pointer type
main.c:554: warning: comparison between pointer and integer
main.c:554: warning: comparison between pointer and integer
main.c:556: error: â&#8364;&#732;optoptâ&#8364;&#8482; undeclared (first use in this function)
main.c:557: warning: comparison between pointer and integer
main.c:557: warning: passing argument 1 of â&#8364;&#732;optslotâ&#8364;&#8482; makes integer from pointer without a cast
main.c:557: error: â&#8364;&#732;struct <anonymous>â&#8364;&#8482; has no member named â&#8364;&#732;has_argâ&#8364;&#8482;
main.c:558: warning: incompatible implicit declaration of built-in function â&#8364;&#732;fprintfâ&#8364;&#8482;
main.c:558: warning: passing argument 1 of â&#8364;&#732;optslotâ&#8364;&#8482; makes integer from pointer without a cast
main.c:558: error: â&#8364;&#732;struct <anonymous>â&#8364;&#8482; has no member named â&#8364;&#732;nameâ&#8364;&#8482;
main.c:558: warning: passing argument 1 of â&#8364;&#732;fprintfâ&#8364;&#8482; discards qualifiers from pointer target type
main.c:558: warning: format â&#8364;&#732;%sâ&#8364;&#8482; expects type â&#8364;&#732;char *â&#8364;&#8482;, but argument 4 has type â&#8364;&#732;const struct <anonymous> *â&#8364;&#8482;
main.c:565: warning: passing argument 2 of â&#8364;&#732;logdebugâ&#8364;&#8482; from incompatible pointer type
main.c:566: warning: comparison between pointer and integer
main.c:566: warning: comparison between pointer and integer
main.c:569: warning: comparison between pointer and integer
main.c:569: warning: passing argument 1 of â&#8364;&#732;optslotâ&#8364;&#8482; makes integer from pointer without a cast
main.c:569: error: â&#8364;&#732;struct <anonymous>â&#8364;&#8482; has no member named â&#8364;&#732;has_argâ&#8364;&#8482;
main.c:570: warning: incompatible implicit declaration of built-in function â&#8364;&#732;fprintfâ&#8364;&#8482;
main.c:570: warning: passing argument 1 of â&#8364;&#732;optslotâ&#8364;&#8482; makes integer from pointer without a cast
main.c:570: error: â&#8364;&#732;struct <anonymous>â&#8364;&#8482; has no member named â&#8364;&#732;nameâ&#8364;&#8482;
main.c:570: warning: passing argument 1 of â&#8364;&#732;fprintfâ&#8364;&#8482; discards qualifiers from pointer target type
main.c:570: warning: format â&#8364;&#732;%sâ&#8364;&#8482; expects type â&#8364;&#732;char *â&#8364;&#8482;, but argument 4 has type â&#8364;&#732;const struct <anonymous> *â&#8364;&#8482;
main.c:572: warning: passing argument 1 of â&#8364;&#732;fprintfâ&#8364;&#8482; discards qualifiers from pointer target type
main.c:572: warning: format â&#8364;&#732;%câ&#8364;&#8482; expects type â&#8364;&#732;intâ&#8364;&#8482;, but argument 4 has type â&#8364;&#732;const struct <anonymous> *â&#8364;&#8482;
main.c:574: warning: implicit declaration of function â&#8364;&#732;strncmpâ&#8364;&#8482;
main.c:574: error: array subscript is not an integer
main.c:575: warning: incompatible implicit declaration of built-in function â&#8364;&#732;fprintfâ&#8364;&#8482;
main.c:575: error: array subscript is not an integer
main.c:575: warning: passing argument 1 of â&#8364;&#732;fprintfâ&#8364;&#8482; discards qualifiers from pointer target type
main.c:575: warning: format â&#8364;&#732;%sâ&#8364;&#8482; expects type â&#8364;&#732;char *â&#8364;&#8482;, but argument 4 has type â&#8364;&#732;const struct <anonymous> *â&#8364;&#8482;
main.c:578: warning: incompatible implicit declaration of built-in function â&#8364;&#732;fprintfâ&#8364;&#8482;
main.c:578: error: array subscript is not an integer
main.c:578: warning: passing argument 1 of â&#8364;&#732;fprintfâ&#8364;&#8482; discards qualifiers from pointer target type
main.c:578: warning: format â&#8364;&#732;%sâ&#8364;&#8482; expects type â&#8364;&#732;char *â&#8364;&#8482;, but argument 4 has type â&#8364;&#732;const struct <anonymous> *â&#8364;&#8482;
main.c:579: warning: passing argument 1 of â&#8364;&#732;fprintfâ&#8364;&#8482; discards qualifiers from pointer target type
main.c:330: warning: unused variable â&#8364;&#732;optionsâ&#8364;&#8482;
main.c: In function â&#8364;&#732;setup_pin_timerâ&#8364;&#8482;:
main.c:601: error: storage size of â&#8364;&#732;ptyeventâ&#8364;&#8482; isnâ&#8364;&#8482;t known
main.c:605: warning: implicit declaration of function â&#8364;&#732;memsetâ&#8364;&#8482;
main.c:605: warning: incompatible implicit declaration of built-in function â&#8364;&#732;memsetâ&#8364;&#8482;
main.c:605: warning: passing argument 3 of â&#8364;&#732;memsetâ&#8364;&#8482; makes integer from pointer without a cast
main.c:608: error: request for member â&#8364;&#732;sigev_signoâ&#8364;&#8482; in something not a structure or union
main.c:608: error: â&#8364;&#732;SIGRTMINâ&#8364;&#8482; undeclared (first use in this function)
main.c:608: warning: statement with no effect
main.c:611: error: request for member â&#8364;&#732;sigev_notifyâ&#8364;&#8482; in something not a structure or union
main.c:611: error: â&#8364;&#732;SIGEV_THREAD_IDâ&#8364;&#8482; undeclared (first use in this function)
main.c:611: warning: statement with no effect
main.c:612: error: request for member â&#8364;&#732;_sigev_unâ&#8364;&#8482; in something not a structure or union
main.c:612: error: request for member â&#8364;&#732;_tidâ&#8364;&#8482; in something not a structure or union
main.c:612: warning: statement with no effect
main.c:614: warning: implicit declaration of function â&#8364;&#732;mtimer_createâ&#8364;&#8482;
main.c:614: error: â&#8364;&#732;CLOCK_REALTIMEâ&#8364;&#8482; undeclared (first use in this function)
main.c:616: warning: passing argument 2 of â&#8364;&#732;logdebugâ&#8364;&#8482; from incompatible pointer type
main.c:621: error: â&#8364;&#732;mtimer_tâ&#8364;&#8482; has no member named â&#8364;&#732;idâ&#8364;&#8482;
main.c:621: warning: passing argument 1 of â&#8364;&#732;logwarnâ&#8364;&#8482; from incompatible pointer type
main.c:622: warning: passing argument 2 of â&#8364;&#732;logsyserrorâ&#8364;&#8482; from incompatible pointer type
main.c:625: warning: passing argument 3 of â&#8364;&#732;memsetâ&#8364;&#8482; makes integer from pointer without a cast
main.c:628: error: request for member â&#8364;&#732;sigev_signoâ&#8364;&#8482; in something not a structure or union
main.c:628: warning: statement with no effect
main.c:629: error: request for member â&#8364;&#732;sigev_notifyâ&#8364;&#8482; in something not a structure or union
main.c:629: error: â&#8364;&#732;SIGEV_SIGNALâ&#8364;&#8482; undeclared (first use in this function)
main.c:629: warning: statement with no effect
main.c:636: error: â&#8364;&#732;mtimer_tâ&#8364;&#8482; has no member named â&#8364;&#732;idâ&#8364;&#8482;
main.c:636: warning: passing argument 1 of â&#8364;&#732;logerrâ&#8364;&#8482; from incompatible pointer type
main.c:640: warning: passing argument 2 of â&#8364;&#732;logdebugâ&#8364;&#8482; from incompatible pointer type
main.c:601: warning: unused variable â&#8364;&#732;ptyeventâ&#8364;&#8482;
main.c: At top level:
main.c:645: error: expected specifier-qualifier-list before â&#8364;&#732;uint8_tâ&#8364;&#8482;
main.c:658: error: expected â&#8364;&#732;=â&#8364;&#8482;, â&#8364;&#732;,â&#8364;&#8482;, â&#8364;&#732;;â&#8364;&#8482;, â&#8364;&#732;asmâ&#8364;&#8482; or â&#8364;&#732;__attribute__â&#8364;&#8482; before â&#8364;&#732;io_uart_msrâ&#8364;&#8482;
main.c:659: error: expected â&#8364;&#732;=â&#8364;&#8482;, â&#8364;&#732;,â&#8364;&#8482;, â&#8364;&#732;;â&#8364;&#8482;, â&#8364;&#732;asmâ&#8364;&#8482; or â&#8364;&#732;__attribute__â&#8364;&#8482; before â&#8364;&#732;io_uart_statusâ&#8364;&#8482;
main.c:663: error: expected â&#8364;&#732;=â&#8364;&#8482;, â&#8364;&#732;,â&#8364;&#8482;, â&#8364;&#732;;â&#8364;&#8482;, â&#8364;&#732;asmâ&#8364;&#8482; or â&#8364;&#732;__attribute__â&#8364;&#8482; before â&#8364;&#732;dp_dsp_statusâ&#8364;&#8482;
main.c:664: error: expected â&#8364;&#732;=â&#8364;&#8482;, â&#8364;&#732;,â&#8364;&#8482;, â&#8364;&#732;;â&#8364;&#8482;, â&#8364;&#732;asmâ&#8364;&#8482; or â&#8364;&#732;__attribute__â&#8364;&#8482; before â&#8364;&#732;dp_wDspRetrainStateâ&#8364;&#8482;
main.c: In function â&#8364;&#732;monitor_stateâ&#8364;&#8482;:
main.c:717: error: â&#8364;&#732;io_uart_msrâ&#8364;&#8482; undeclared (first use in this function)
main.c:717: error: â&#8364;&#732;struct _stateâ&#8364;&#8482; has no member named â&#8364;&#732;io_uart_msrâ&#8364;&#8482;
main.c:717: warning: implicit declaration of function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:717: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:717: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:717: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:717: warning: implicit declaration of function â&#8364;&#732;__STRINGâ&#8364;&#8482;
main.c:717: error: expected â&#8364;&#732;)â&#8364;&#8482; before string constant
main.c:717: warning: passing argument 2 of â&#8364;&#732;sprintfâ&#8364;&#8482; makes pointer from integer without a cast
main.c:717: error: â&#8364;&#732;struct _stateâ&#8364;&#8482; has no member named â&#8364;&#732;io_uart_msrâ&#8364;&#8482;
main.c:717: warning: statement with no effect
main.c:718: error: â&#8364;&#732;io_uart_statusâ&#8364;&#8482; undeclared (first use in this function)
main.c:718: error: â&#8364;&#732;struct _stateâ&#8364;&#8482; has no member named â&#8364;&#732;io_uart_statusâ&#8364;&#8482;
main.c:718: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:718: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:718: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:718: error: expected â&#8364;&#732;)â&#8364;&#8482; before string constant
main.c:718: warning: passing argument 2 of â&#8364;&#732;sprintfâ&#8364;&#8482; makes pointer from integer without a cast
main.c:718: error: â&#8364;&#732;struct _stateâ&#8364;&#8482; has no member named â&#8364;&#732;io_uart_statusâ&#8364;&#8482;
main.c:718: warning: statement with no effect
main.c:719: error: â&#8364;&#732;struct _stateâ&#8364;&#8482; has no member named â&#8364;&#732;x_modem_stateâ&#8364;&#8482;
main.c:719: warning: comparison between pointer and integer
main.c:719: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:719: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:719: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:719: error: expected â&#8364;&#732;)â&#8364;&#8482; before string constant
main.c:719: warning: passing argument 2 of â&#8364;&#732;sprintfâ&#8364;&#8482; makes pointer from integer without a cast
main.c:719: error: â&#8364;&#732;struct _stateâ&#8364;&#8482; has no member named â&#8364;&#732;x_modem_stateâ&#8364;&#8482;
main.c:719: warning: statement with no effect
main.c:720: error: â&#8364;&#732;struct _stateâ&#8364;&#8482; has no member named â&#8364;&#732;x_modem_modeâ&#8364;&#8482;
main.c:720: warning: comparison between pointer and integer
main.c:720: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:720: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:720: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:720: error: expected â&#8364;&#732;)â&#8364;&#8482; before string constant
main.c:720: warning: passing argument 2 of â&#8364;&#732;sprintfâ&#8364;&#8482; makes pointer from integer without a cast
main.c:720: error: â&#8364;&#732;struct _stateâ&#8364;&#8482; has no member named â&#8364;&#732;x_modem_modeâ&#8364;&#8482;
main.c:720: warning: statement with no effect
main.c:721: error: â&#8364;&#732;struct _stateâ&#8364;&#8482; has no member named â&#8364;&#732;x_line_rateâ&#8364;&#8482;
main.c:721: warning: comparison between pointer and integer
main.c:721: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:721: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:721: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:721: error: expected â&#8364;&#732;)â&#8364;&#8482; before string constant
main.c:721: warning: passing argument 2 of â&#8364;&#732;sprintfâ&#8364;&#8482; makes pointer from integer without a cast
main.c:721: error: â&#8364;&#732;struct _stateâ&#8364;&#8482; has no member named â&#8364;&#732;x_line_rateâ&#8364;&#8482;
main.c:721: warning: statement with no effect
main.c:722: error: â&#8364;&#732;dp_dsp_statusâ&#8364;&#8482; undeclared (first use in this function)
main.c:722: error: â&#8364;&#732;struct _stateâ&#8364;&#8482; has no member named â&#8364;&#732;dp_dsp_statusâ&#8364;&#8482;
main.c:722: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:722: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:722: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:722: error: expected â&#8364;&#732;)â&#8364;&#8482; before string constant
main.c:722: warning: passing argument 2 of â&#8364;&#732;sprintfâ&#8364;&#8482; makes pointer from integer without a cast
main.c:722: error: â&#8364;&#732;struct _stateâ&#8364;&#8482; has no member named â&#8364;&#732;dp_dsp_statusâ&#8364;&#8482;
main.c:722: warning: statement with no effect
main.c:723: error: â&#8364;&#732;struct _stateâ&#8364;&#8482; has no member named â&#8364;&#732;io_app_tx_countâ&#8364;&#8482;
main.c:723: warning: comparison between pointer and integer
main.c:723: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:723: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:723: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:723: error: expected â&#8364;&#732;)â&#8364;&#8482; before string constant
main.c:723: warning: passing argument 2 of â&#8364;&#732;sprintfâ&#8364;&#8482; makes pointer from integer without a cast
main.c:723: error: â&#8364;&#732;struct _stateâ&#8364;&#8482; has no member named â&#8364;&#732;io_app_tx_countâ&#8364;&#8482;
main.c:723: warning: statement with no effect
main.c:725: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:726: warning: passing argument 2 of â&#8364;&#732;logdebugâ&#8364;&#8482; from incompatible pointer type
main.c:730: error: â&#8364;&#732;struct _stateâ&#8364;&#8482; has no member named â&#8364;&#732;io_app_tx_bytesâ&#8364;&#8482;
main.c:730: warning: comparison between pointer and integer
main.c:730: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:730: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:730: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:730: error: â&#8364;&#732;io_app_txâ&#8364;&#8482; undeclared (first use in this function)
main.c:730: error: expected â&#8364;&#732;)â&#8364;&#8482; before string constant
main.c:730: warning: passing argument 2 of â&#8364;&#732;sprintfâ&#8364;&#8482; makes pointer from integer without a cast
main.c:730: error: â&#8364;&#732;struct _stateâ&#8364;&#8482; has no member named â&#8364;&#732;io_app_tx_bytesâ&#8364;&#8482;
main.c:730: warning: statement with no effect
main.c:731: error: â&#8364;&#732;struct _stateâ&#8364;&#8482; has no member named â&#8364;&#732;io_dte_tx_bytesâ&#8364;&#8482;
main.c:731: warning: comparison between pointer and integer
main.c:731: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:731: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:731: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:731: error: â&#8364;&#732;io_dte_txâ&#8364;&#8482; undeclared (first use in this function)
main.c:731: error: expected â&#8364;&#732;)â&#8364;&#8482; before string constant
main.c:731: warning: passing argument 2 of â&#8364;&#732;sprintfâ&#8364;&#8482; makes pointer from integer without a cast
main.c:731: error: â&#8364;&#732;struct _stateâ&#8364;&#8482; has no member named â&#8364;&#732;io_dte_tx_bytesâ&#8364;&#8482;
main.c:731: warning: statement with no effect
main.c:732: error: â&#8364;&#732;struct _stateâ&#8364;&#8482; has no member named â&#8364;&#732;io_dte_rx_bytesâ&#8364;&#8482;
main.c:732: warning: comparison between pointer and integer
main.c:732: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:732: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:732: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:732: error: â&#8364;&#732;io_dte_rxâ&#8364;&#8482; undeclared (first use in this function)
main.c:732: error: expected â&#8364;&#732;)â&#8364;&#8482; before string constant
main.c:732: warning: passing argument 2 of â&#8364;&#732;sprintfâ&#8364;&#8482; makes pointer from integer without a cast
main.c:732: error: â&#8364;&#732;struct _stateâ&#8364;&#8482; has no member named â&#8364;&#732;io_dte_rx_bytesâ&#8364;&#8482;
main.c:732: warning: statement with no effect
main.c:733: error: â&#8364;&#732;struct _stateâ&#8364;&#8482; has no member named â&#8364;&#732;io_dce_tx_bytesâ&#8364;&#8482;
main.c:733: warning: comparison between pointer and integer
main.c:733: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:733: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:733: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:733: error: â&#8364;&#732;io_dce_txâ&#8364;&#8482; undeclared (first use in this function)
main.c:733: error: expected â&#8364;&#732;)â&#8364;&#8482; before string constant
main.c:733: warning: passing argument 2 of â&#8364;&#732;sprintfâ&#8364;&#8482; makes pointer from integer without a cast
main.c:733: error: â&#8364;&#732;struct _stateâ&#8364;&#8482; has no member named â&#8364;&#732;io_dce_tx_bytesâ&#8364;&#8482;
main.c:733: warning: statement with no effect
main.c:734: error: â&#8364;&#732;struct _stateâ&#8364;&#8482; has no member named â&#8364;&#732;io_dce_rx_bytesâ&#8364;&#8482;
main.c:734: warning: comparison between pointer and integer
main.c:734: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:734: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:734: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:734: error: â&#8364;&#732;io_dce_rxâ&#8364;&#8482; undeclared (first use in this function)
main.c:734: error: expected â&#8364;&#732;)â&#8364;&#8482; before string constant
main.c:734: warning: passing argument 2 of â&#8364;&#732;sprintfâ&#8364;&#8482; makes pointer from integer without a cast
main.c:734: error: â&#8364;&#732;struct _stateâ&#8364;&#8482; has no member named â&#8364;&#732;io_dce_rx_bytesâ&#8364;&#8482;
main.c:734: warning: statement with no effect
main.c:736: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
main.c:737: warning: passing argument 2 of â&#8364;&#732;logdebugâ&#8364;&#8482; from incompatible pointer type
main.c: In function â&#8364;&#732;setup_pin_watcherâ&#8364;&#8482;:
main.c:758: error: storage size of â&#8364;&#732;timer_actionâ&#8364;&#8482; isnâ&#8364;&#8482;t known
main.c:760: error: request for member â&#8364;&#732;sa_handlerâ&#8364;&#8482; in something not a structure or union
main.c:760: warning: statement with no effect
main.c:761: error: request for member â&#8364;&#732;sa_flagsâ&#8364;&#8482; in something not a structure or union
main.c:761: warning: statement with no effect
main.c:762: warning: implicit declaration of function â&#8364;&#732;sigemptysetâ&#8364;&#8482;
main.c:762: error: request for member â&#8364;&#732;sa_maskâ&#8364;&#8482; in something not a structure or union
main.c:763: warning: implicit declaration of function â&#8364;&#732;sigactionâ&#8364;&#8482;
main.c:763: error: â&#8364;&#732;SIGRTMINâ&#8364;&#8482; undeclared (first use in this function)
main.c:758: warning: unused variable â&#8364;&#732;timer_actionâ&#8364;&#8482;
main.c:766:19: error: errno.h: No such file or directory
main.c: At top level:
main.c:769: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
main.c: In function â&#8364;&#732;mainâ&#8364;&#8482;:
main.c:837: error: â&#8364;&#732;struct _configâ&#8364;&#8482; has no member named â&#8364;&#732;syslogâ&#8364;&#8482;
main.c:840: error: â&#8364;&#732;struct _configâ&#8364;&#8482; has no member named â&#8364;&#732;daemonâ&#8364;&#8482;
main.c:841: warning: implicit declaration of function â&#8364;&#732;daemonâ&#8364;&#8482;
main.c:841: error: â&#8364;&#732;struct _configâ&#8364;&#8482; has no member named â&#8364;&#732;logfileâ&#8364;&#8482;
main.c:843: warning: passing argument 2 of â&#8364;&#732;logsyserrorâ&#8364;&#8482; from incompatible pointer type
main.c:844: warning: passing argument 1 of â&#8364;&#732;logwarnâ&#8364;&#8482; from incompatible pointer type
main.c:845: error: â&#8364;&#732;struct _configâ&#8364;&#8482; has no member named â&#8364;&#732;daemonâ&#8364;&#8482;
main.c:845: warning: statement with no effect
main.c:848: error: â&#8364;&#732;struct _configâ&#8364;&#8482; has no member named â&#8364;&#732;daemonâ&#8364;&#8482;
main.c:848: error: â&#8364;&#732;struct _configâ&#8364;&#8482; has no member named â&#8364;&#732;logfileâ&#8364;&#8482;
main.c:849: error: â&#8364;&#732;struct _configâ&#8364;&#8482; has no member named â&#8364;&#732;syslogâ&#8364;&#8482;
main.c:849: warning: statement with no effect
main.c:852: warning: passing argument 2 of â&#8364;&#732;logdebugâ&#8364;&#8482; from incompatible pointer type
main.c:862: warning: passing argument 2 of â&#8364;&#732;logdebugâ&#8364;&#8482; from incompatible pointer type
main.c:871: warning: implicit declaration of function â&#8364;&#732;snprintfâ&#8364;&#8482;
main.c:871: warning: incompatible implicit declaration of built-in function â&#8364;&#732;snprintfâ&#8364;&#8482;
main.c:874: warning: incompatible implicit declaration of built-in function â&#8364;&#732;snprintfâ&#8364;&#8482;
main.c:878: warning: incompatible implicit declaration of built-in function â&#8364;&#732;snprintfâ&#8364;&#8482;
main.c:880: warning: implicit declaration of function â&#8364;&#732;strlenâ&#8364;&#8482;
main.c:880: warning: incompatible implicit declaration of built-in function â&#8364;&#732;strlenâ&#8364;&#8482;
main.c:885: warning: passing argument 2 of â&#8364;&#732;logdebugâ&#8364;&#8482; from incompatible pointer type
main.c:888: error: â&#8364;&#732;struct _configâ&#8364;&#8482; has no member named â&#8364;&#732;misrâ&#8364;&#8482;
main.c:888: error: incompatible type for argument 1 of â&#8364;&#732;misr_strâ&#8364;&#8482;
main.c:888: error: â&#8364;&#732;struct _configâ&#8364;&#8482; has no member named â&#8364;&#732;realtimeâ&#8364;&#8482;
main.c:888: warning: passing argument 2 of â&#8364;&#732;logdebugâ&#8364;&#8482; from incompatible pointer type
main.c:909: warning: passing argument 2 of â&#8364;&#732;mthread_createâ&#8364;&#8482; discards qualifiers from pointer target type
main.c:910: warning: passing argument 1 of â&#8364;&#732;logerrâ&#8364;&#8482; from incompatible pointer type
main.c:913: warning: passing argument 2 of â&#8364;&#732;logdebugâ&#8364;&#8482; from incompatible pointer type
main.c:924: warning: passing argument 1 of â&#8364;&#732;loginfoâ&#8364;&#8482; from incompatible pointer type
main.c:928: warning: passing argument 2 of â&#8364;&#732;logdebugâ&#8364;&#8482; from incompatible pointer type
main.c:933: warning: implicit declaration of function â&#8364;&#732;mkfifoâ&#8364;&#8482;
main.c:934: error: â&#8364;&#732;errnoâ&#8364;&#8482; undeclared (first use in this function)
main.c:934: error: â&#8364;&#732;EEXISTâ&#8364;&#8482; undeclared (first use in this function)
main.c:935: warning: passing argument 2 of â&#8364;&#732;logdebugâ&#8364;&#8482; from incompatible pointer type
main.c:937: warning: passing argument 2 of â&#8364;&#732;logsyserrorâ&#8364;&#8482; from incompatible pointer type
main.c:940: error: â&#8364;&#732;FILEâ&#8364;&#8482; undeclared (first use in this function)
main.c:940: error: â&#8364;&#732;controlâ&#8364;&#8482; undeclared (first use in this function)
main.c:940: error: invalid operands to binary *
main.c:940: warning: statement with no effect
main.c:943: warning: implicit declaration of function â&#8364;&#732;fopenâ&#8364;&#8482;
main.c:943: warning: statement with no effect
main.c:944: error: â&#8364;&#732;EINTRâ&#8364;&#8482; undeclared (first use in this function)
main.c:950: warning: passing argument 2 of â&#8364;&#732;logsyserrorâ&#8364;&#8482; from incompatible pointer type
main.c:951: warning: passing argument 1 of â&#8364;&#732;logwarnâ&#8364;&#8482; from incompatible pointer type
main.c:958: warning: implicit declaration of function â&#8364;&#732;get_cmdâ&#8364;&#8482;
main.c:961: warning: passing argument 2 of â&#8364;&#732;logdebugâ&#8364;&#8482; from incompatible pointer type
main.c:962: warning: implicit declaration of function â&#8364;&#732;fcloseâ&#8364;&#8482;
main.c:964: warning: statement with no effect
main.c:971: warning: passing argument 2 of â&#8364;&#732;logsyserrorâ&#8364;&#8482; from incompatible pointer type
main.c:972: warning: passing argument 1 of â&#8364;&#732;logwarnâ&#8364;&#8482; from incompatible pointer type
main.c:978: warning: passing argument 1 of â&#8364;&#732;loginfoâ&#8364;&#8482; from incompatible pointer type
main.c:984: error: â&#8364;&#732;__u32â&#8364;&#8482; undeclared (first use in this function)
main.c:984: error: expected expression before â&#8364;&#732;)â&#8364;&#8482; token
main.c:984: error: invalid operands to binary *
main.c:984: error: called object â&#8364;&#732;<erroneous-expression>â&#8364;&#8482; is not a function
main.c:984: error: assignment of read-only location
main.c:984: error: incompatible types in assignment
main.c:984: warning: statement with no effect
main.c:985: error: â&#8364;&#732;__u16â&#8364;&#8482; undeclared (first use in this function)
main.c:985: error: expected expression before â&#8364;&#732;)â&#8364;&#8482; token
main.c:985: error: invalid operands to binary *
main.c:985: error: called object â&#8364;&#732;<erroneous-expression>â&#8364;&#8482; is not a function
main.c:985: error: assignment of read-only location
main.c:985: error: incompatible types in assignment
main.c:985: warning: statement with no effect
main.c:992: warning: passing argument 1 of â&#8364;&#732;loginfoâ&#8364;&#8482; from incompatible pointer type
main.c:993: warning: implicit declaration of function â&#8364;&#732;ioctlâ&#8364;&#8482;
main.c:993: warning: implicit declaration of function â&#8364;&#732;_IOâ&#8364;&#8482;
main.c:995: warning: passing argument 2 of â&#8364;&#732;logsyserrorâ&#8364;&#8482; from incompatible pointer type
main.c:999: warning: passing argument 1 of â&#8364;&#732;loginfoâ&#8364;&#8482; from incompatible pointer type
main.c:1002: warning: passing argument 2 of â&#8364;&#732;logsyserrorâ&#8364;&#8482; from incompatible pointer type
main.c:1005: warning: passing argument 2 of â&#8364;&#732;logdebugâ&#8364;&#8482; from incompatible pointer type
main.c:1013: warning: implicit declaration of function â&#8364;&#732;pauseâ&#8364;&#8482;
main.c: In function â&#8364;&#732;serve_portâ&#8364;&#8482;:
main.c:1029: warning: passing argument 2 of â&#8364;&#732;logdebugâ&#8364;&#8482; from incompatible pointer type
main.c:1031: error: â&#8364;&#732;struct _configâ&#8364;&#8482; has no member named â&#8364;&#732;realtimeâ&#8364;&#8482;
main.c:1041: warning: passing argument 1 of â&#8364;&#732;logerrâ&#8364;&#8482; from incompatible pointer type
main.c:1042: warning: incompatible implicit declaration of built-in function â&#8364;&#732;exitâ&#8364;&#8482;
main.c:1047: warning: passing argument 1 of â&#8364;&#732;logerrâ&#8364;&#8482; from incompatible pointer type
main.c:1050: warning: passing argument 2 of â&#8364;&#732;logdebugâ&#8364;&#8482; from incompatible pointer type
main.c:1055: warning: passing argument 2 of â&#8364;&#732;logdebugâ&#8364;&#8482; from incompatible pointer type
main.c: In function â&#8364;&#732;mexitâ&#8364;&#8482;:
main.c:1082: error: â&#8364;&#732;struct _configâ&#8364;&#8482; has no member named â&#8364;&#732;daemonâ&#8364;&#8482;
main.c:1083: warning: passing argument 1 of â&#8364;&#732;loginfoâ&#8364;&#8482; from incompatible pointer type
main.c:1085: warning: passing argument 1 of â&#8364;&#732;loginfoâ&#8364;&#8482; from incompatible pointer type
main.c:1086: warning: incompatible implicit declaration of built-in function â&#8364;&#732;exitâ&#8364;&#8482;
main.c: In function â&#8364;&#732;kbdint_handlerâ&#8364;&#8482;:
main.c:1093: warning: passing argument 2 of â&#8364;&#732;logdebugâ&#8364;&#8482; from incompatible pointer type
main.c: In function â&#8364;&#732;setup_kbd_interruptâ&#8364;&#8482;:
main.c:1098: error: storage size of â&#8364;&#732;timer_actionâ&#8364;&#8482; isnâ&#8364;&#8482;t known
main.c:1100: error: request for member â&#8364;&#732;sa_handlerâ&#8364;&#8482; in something not a structure or union
main.c:1100: warning: statement with no effect
main.c:1101: error: request for member â&#8364;&#732;sa_flagsâ&#8364;&#8482; in something not a structure or union
main.c:1101: warning: statement with no effect
main.c:1102: error: request for member â&#8364;&#732;sa_maskâ&#8364;&#8482; in something not a structure or union
main.c:1103: error: â&#8364;&#732;SIGINTâ&#8364;&#8482; undeclared (first use in this function)
main.c:1098: warning: unused variable â&#8364;&#732;timer_actionâ&#8364;&#8482;
main.c: In function â&#8364;&#732;sigterm_handlerâ&#8364;&#8482;:
main.c:1107: warning: passing argument 2 of â&#8364;&#732;logdebugâ&#8364;&#8482; from incompatible pointer type
main.c: In function â&#8364;&#732;setup_daemon_signalsâ&#8364;&#8482;:
main.c:1112: error: storage size of â&#8364;&#732;timer_actionâ&#8364;&#8482; isnâ&#8364;&#8482;t known
main.c:1114: error: request for member â&#8364;&#732;sa_handlerâ&#8364;&#8482; in something not a structure or union
main.c:1114: warning: statement with no effect
main.c:1115: error: request for member â&#8364;&#732;sa_flagsâ&#8364;&#8482; in something not a structure or union
main.c:1115: warning: statement with no effect
main.c:1116: error: request for member â&#8364;&#732;sa_maskâ&#8364;&#8482; in something not a structure or union
main.c:1117: error: â&#8364;&#732;SIGTERMâ&#8364;&#8482; undeclared (first use in this function)
main.c:1112: warning: unused variable â&#8364;&#732;timer_actionâ&#8364;&#8482;
main.c: In function â&#8364;&#732;setup_segvâ&#8364;&#8482;:
main.c:1124: error: storage size of â&#8364;&#732;actionâ&#8364;&#8482; isnâ&#8364;&#8482;t known
main.c:1126: error: request for member â&#8364;&#732;sa_handlerâ&#8364;&#8482; in something not a structure or union
main.c:1126: warning: statement with no effect
main.c:1127: error: request for member â&#8364;&#732;sa_flagsâ&#8364;&#8482; in something not a structure or union
main.c:1127: warning: statement with no effect
main.c:1128: error: request for member â&#8364;&#732;sa_maskâ&#8364;&#8482; in something not a structure or union
main.c:1129: error: â&#8364;&#732;SIGSEGVâ&#8364;&#8482; undeclared (first use in this function)
main.c:1124: warning: unused variable â&#8364;&#732;actionâ&#8364;&#8482;
main.c: In function â&#8364;&#732;segv_handlerâ&#8364;&#8482;:
main.c:1133: error: storage size of â&#8364;&#732;actionâ&#8364;&#8482; isnâ&#8364;&#8482;t known
main.c:1136: warning: incompatible implicit declaration of built-in function â&#8364;&#732;printfâ&#8364;&#8482;
main.c:1138: error: request for member â&#8364;&#732;sa_handlerâ&#8364;&#8482; in something not a structure or union
main.c:1138: error: â&#8364;&#732;SIG_DFLâ&#8364;&#8482; undeclared (first use in this function)
main.c:1138: warning: statement with no effect
main.c:1139: error: request for member â&#8364;&#732;sa_flagsâ&#8364;&#8482; in something not a structure or union
main.c:1139: warning: statement with no effect
main.c:1140: error: request for member â&#8364;&#732;sa_maskâ&#8364;&#8482; in something not a structure or union
main.c:1141: error: â&#8364;&#732;SIGSEGVâ&#8364;&#8482; undeclared (first use in this function)
main.c:1133: warning: unused variable â&#8364;&#732;actionâ&#8364;&#8482;
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/home/teriwood/Desktop/martain/modem'
make: *** [install] Error 2
teriwood@teriwood-desktop:~/Desktop/martain$

```

---

### Post by The Titan on 2008-04-05
looks like you have to install build essentials as above, and for future reference, wrap something huge like that in code tags... nobody likes to see a huge post like that.

---

### Post by teriwood on 2008-04-05
Okay, good -- it looks like you guys know what I'm doing wrong.  But I have two more questions.

Spiderbatdad says:
"Also is there a ./configure step first, as outlined in the readme file? There maybe a number of errors there as a result of lacking the build tools. The build-essential package is usually needed for installing third-party software."

I'm not sure what this is.  Which readme file?  I don't see it in the readme file in the martian folder.  Is this another file I need to download?  Or did I just miss a step?  I don't see a ./configure on the martian update page.  

The Titan says:
"...for future reference, wrap something huge like that in code tags... nobody likes to see a huge post like that."

How do I do that exactly?  I'll be happy to go back and edit that post -- it is ... horrible like that ... but I don't know how to do that?

And thanks again, to both of you.
It is appreciated!

Teri

---

### Post by The Titan on 2008-04-05
first, ./configure executes the file "configure"  It is almost always done when compiling something from source which is what your doing FYI, not sure your skill level

second just do {CODE} at the beginning and {/CODE} at the end, but instead of { and } use [ and ]

---

### Post by spiderbatdad on 2008-04-05
Don't sweat it. The little # symbols in the editor here will provide a set of  tags that look like :{code}{/code}  paste your output inside those then move the cursor beyond the closing tag.

Edited in favor of next post.

---

### Post by spiderbatdad on 2008-04-05
See here: [https://help.ubuntu.com/community/DialupModemHowto/Lucent](https://help.ubuntu.com/community/DialupModemHowto/Lucent)

---

### Post by teriwood on 2008-04-05
> **The Titan said:**
> first, ./configure executes the file "configure"  It is almost always done when compiling something from source which is what your doing FYI, not sure your skill level


My skill level is "crap".  I'm learning this today as I go along.

So ... I need to include the ./configure command in there somewhere.  At what point do I put it in?

The commands I see listed from the instruction page are:

[COLOR="DarkGreen"]
$ ls
$ cp FromSomewhere/ltmdmobj.o  modem/
$ make clean
$ make
$ ls -l kmodule/*.ko
$ ls -l  modem/martian*
$ sudo make install
[/COLOR]

which is where I stalled out with the errors above.

Again, thanks so much.  This really is the first time I've done anything like this, and that I got this far at all amazes me.  

Awaiting your next replies with baited breath.  And hanging on every word.

Teri

---

### Post by teriwood on 2008-04-06
Hi again! And I have a new error message after trying the last command.

```
main.c:188: warning: (near initialization for â€˜IdtoCodeFix[7]â€™)
main.c:189: warning: excess elements in struct initializer
main.c:189: warning: (near initialization for â€˜IdtoCodeFix[8]â€™)
main.c:189: warning: excess elements in struct initializer
main.c:189: warning: (near initialization for â€˜IdtoCodeFix[8]â€™)
main.c:190: warning: excess elements in struct initializer
main.c:190: warning: (near initialization for â€˜IdtoCodeFix[9]â€™)
main.c:190: warning: excess elements in struct initializer
main.c:190: warning: (near initialization for â€˜IdtoCodeFix[9]â€™)
main.c:194: warning: division by zero
main.c:195: error: â€˜struct <anonymous>â€™ has no member named â€˜idâ€™
main.c:195: error: â€˜struct <anonymous>â€™ has no member named â€˜codeâ€™
main.c: At top level:
main.c:301: error: â€˜NULLâ€™ undeclared here (not in a function)
main.c: In function â€˜mcountry_matchâ€™:
main.c:306: warning: implicit declaration of function â€˜strchrâ€™
main.c:306: warning: incompatible implicit declaration of built-in function â€˜strchrâ€™
main.c:309: warning: implicit declaration of function â€˜strncasecmpâ€™
main.c:312: warning: implicit declaration of function â€˜strcasecmpâ€™
main.c: In function â€˜parse_argumentsâ€™:
main.c:330: error: array type has incomplete element type
main.c:331: error: â€˜required_argumentâ€™ undeclared (first use in this function)
main.c:332: error: â€˜no_argumentâ€™ undeclared (first use in this function)
main.c:353: error: â€˜struct _configâ€™ has no member named â€˜realtimeâ€™
main.c:353: warning: statement with no effect
main.c:354: error: â€˜struct _configâ€™ has no member named â€˜syslogâ€™
main.c:354: warning: statement with no effect
main.c:355: error: â€˜struct _configâ€™ has no member named â€˜daemonâ€™
main.c:355: warning: statement with no effect
main.c:356: error: â€˜struct _configâ€™ has no member named â€˜logfileâ€™
main.c:356: warning: statement with no effect
main.c:357: error: â€˜struct _configâ€™ has no member named â€˜check_carrierâ€™
main.c:357: warning: statement with no effect
main.c:359: error: â€˜struct _configâ€™ has no member named â€˜misrâ€™
main.c:359: warning: statement with no effect
main.c:360: error: â€˜struct _configâ€™ has no member named â€˜hide_ptyâ€™
main.c:360: warning: statement with no effect
main.c:361: error: â€˜struct _configâ€™ has no member named â€˜true_smpâ€™
main.c:361: warning: statement with no effect
main.c:362: error: â€˜struct _configâ€™ has no member named â€˜move_fifosâ€™
main.c:362: warning: statement with no effect
main.c:364: error: â€˜struct _configâ€™ has no member named â€˜permissionsâ€™
main.c:364: warning: statement with no effect
main.c:365: error: â€˜struct _configâ€™ has no member named â€˜modeâ€™
main.c:365: warning: statement with no effect
main.c:367: error: â€˜struct _configâ€™ has no member named â€˜uidâ€™
main.c:367: warning: statement with no effect
main.c:368: error: â€˜struct _configâ€™ has no member named â€˜gidâ€™
main.c:368: warning: statement with no effect
main.c:372: error: â€˜opterrâ€™ undeclared (first use in this function)
main.c:372: warning: statement with no effect
main.c:375: warning: implicit declaration of function â€˜getopt_longâ€™
main.c:379: error: â€˜struct _configâ€™ has no member named â€˜realtimeâ€™
main.c:379: warning: statement with no effect
main.c:384: warning: implicit declaration of function â€˜strcmpâ€™
main.c:384: error: â€˜optargâ€™ undeclared (first use in this function)
main.c:385: error: â€˜struct _configâ€™ has no member named â€˜misrâ€™
main.c:385: warning: statement with no effect
main.c:388: error: â€˜struct _configâ€™ has no member named â€˜misrâ€™
main.c:388: warning: statement with no effect
main.c:391: warning: passing argument 1 of â€˜logerrâ€™ from incompatible pointer type
main.c:392: warning: incompatible implicit declaration of built-in function â€˜fprintfâ€™
main.c:392: error: â€˜stderrâ€™ undeclared (first use in this function)
main.c:392: warning: passing argument 1 of â€˜fprintfâ€™ discards qualifiers from pointer target type
main.c:398: error: â€˜struct _configâ€™ has no member named â€˜syslogâ€™
main.c:399: warning: passing argument 1 of â€˜logerrâ€™ from incompatible pointer type
main.c:402: error: â€˜struct _configâ€™ has no member named â€˜logfileâ€™
main.c:402: warning: statement with no effect
main.c:403: warning: passing argument 1 of â€˜log_redirect_to_fileâ€™ from incompatible pointer type
main.c:406: warning: passing argument 1 of â€˜logwarnâ€™ from incompatible pointer type
main.c:410: warning: passing argument 1 of â€˜logwarnâ€™ from incompatible pointer type
main.c:416: warning: assignment from incompatible pointer type
main.c:420: warning: implicit declaration of function â€˜atoiâ€™
main.c:422: warning: passing argument 1 of â€˜logwarnâ€™ from incompatible pointer type
main.c:428: error: â€˜struct _configâ€™ has no member named â€˜daemonâ€™
main.c:428: warning: statement with no effect
main.c:434: error: â€˜struct _configâ€™ has no member named â€˜logfileâ€™
main.c:435: warning: passing argument 1 of â€˜logerrâ€™ from incompatible pointer type
main.c:438: error: â€˜struct _configâ€™ has no member named â€˜syslogâ€™
main.c:438: warning: statement with no effect
main.c:447: error: â€˜struct _configâ€™ has no member named â€˜check_carrierâ€™
main.c:447: warning: statement with no effect
main.c:451: error: â€˜struct _configâ€™ has no member named â€˜hide_ptyâ€™
main.c:451: warning: statement with no effect
main.c:455: error: â€˜struct _configâ€™ has no member named â€˜true_smpâ€™
main.c:455: warning: statement with no effect
main.c:459: error: â€˜struct _configâ€™ has no member named â€˜move_fifosâ€™
main.c:459: warning: statement with no effect
main.c:464: warning: implicit declaration of function â€˜getpwnamâ€™
main.c:464: warning: initialization makes pointer from integer without a cast
main.c:467: warning: passing argument 1 of â€˜logwarnâ€™ from incompatible pointer type
main.c:469: error: â€˜struct _configâ€™ has no member named â€˜uidâ€™
main.c:469: error: dereferencing pointer to incomplete type
main.c:469: error: request for member â€˜pw_uidâ€™ in something not a structure or union
main.c:469: warning: statement with no effect
main.c:476: warning: implicit declaration of function â€˜getgrnamâ€™
main.c:476: warning: initialization makes pointer from integer without a cast
main.c:479: warning: passing argument 1 of â€˜logwarnâ€™ from incompatible pointer type
main.c:481: error: â€˜struct _configâ€™ has no member named â€˜gidâ€™
main.c:481: error: dereferencing pointer to incomplete type
main.c:481: error: request for member â€˜gr_gidâ€™ in something not a structure or union
main.c:481: warning: statement with no effect
main.c:487: error: â€˜struct _configâ€™ has no member named â€˜modeâ€™
main.c:487: warning: implicit declaration of function â€˜strtolâ€™
main.c:487: warning: statement with no effect
main.c:488: error: â€˜struct _configâ€™ has no member named â€˜modeâ€™
main.c:488: error: â€˜S_IRWXUâ€™ undeclared (first use in this function)
main.c:488: error: â€˜S_IRWXGâ€™ undeclared (first use in this function)
main.c:488: error: invalid operands to binary |
main.c:488: error: â€˜S_IRWXOâ€™ undeclared (first use in this function)
main.c:488: error: invalid operands to binary |
main.c:488: error: wrong type argument to bit-complement
main.c:488: error: invalid operands to binary &
main.c:489: error: â€˜struct _configâ€™ has no member named â€˜modeâ€™
main.c:489: warning: passing argument 1 of â€˜logwarnâ€™ from incompatible pointer type
main.c:490: error: â€˜struct _configâ€™ has no member named â€˜permissionsâ€™
main.c:490: warning: statement with no effect
main.c:493: error: â€˜struct _configâ€™ has no member named â€˜permissionsâ€™
main.c:493: warning: statement with no effect
main.c:501: warning: passing argument 1 of â€˜mcountry_matchâ€™ from incompatible pointer type
main.c:503: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜OldCountryIdToCountryCodeâ€™
main.c:503: error: â€˜OldCountryIdToCountryCodeâ€™ undeclared (first use in this function)
main.c:503: warning: statement with no effect
main.c:507: error: invalid operands to binary ==
main.c:508: warning: passing argument 2 of â€˜logdebugâ€™ from incompatible pointer type
main.c:509: error: â€˜struct _configâ€™ has no member named â€˜country_idâ€™
main.c:509: warning: statement with no effect
main.c:514: warning: passing argument 1 of â€˜logwarnâ€™ from incompatible pointer type
main.c:515: error: â€˜struct _configâ€™ has no member named â€˜country_idâ€™
main.c:515: warning: statement with no effect
main.c:523: warning: passing argument 1 of â€˜logwarnâ€™ from incompatible pointer type
main.c:524: error: â€˜struct _configâ€™ has no member named â€˜country_idâ€™
main.c:524: warning: statement with no effect
main.c:530: warning: pointer type mismatch in conditional expression
main.c:530: warning: passing argument 2 of â€˜logdebugâ€™ from incompatible pointer type
main.c:533: warning: implicit declaration of function â€˜printfâ€™
main.c:533: warning: incompatible implicit declaration of built-in function â€˜printfâ€™
main.c:538: warning: passing argument 1 of â€˜logwarnâ€™ from incompatible pointer type
main.c:541: warning: incompatible implicit declaration of built-in function â€˜exitâ€™
main.c:544: error: â€˜optindâ€™ undeclared (first use in this function)
main.c:544: warning: comparison between pointer and integer
main.c:545: error: array subscript is not an integer
main.c:545: warning: assignment from incompatible pointer type
main.c:547: warning: comparison between pointer and integer
main.c:548: warning: passing argument 1 of â€˜logwarnâ€™ from incompatible pointer type
main.c:554: warning: comparison between pointer and integer
main.c:554: warning: comparison between pointer and integer
main.c:556: error: â€˜optoptâ€™ undeclared (first use in this function)
main.c:557: warning: comparison between pointer and integer
main.c:557: warning: passing argument 1 of â€˜optslotâ€™ makes integer from pointer without a cast
main.c:557: error: â€˜struct <anonymous>â€™ has no member named â€˜has_argâ€™
main.c:558: warning: incompatible implicit declaration of built-in function â€˜fprintfâ€™
main.c:558: warning: passing argument 1 of â€˜optslotâ€™ makes integer from pointer without a cast
main.c:558: error: â€˜struct <anonymous>â€™ has no member named â€˜nameâ€™
main.c:558: warning: passing argument 1 of â€˜fprintfâ€™ discards qualifiers from pointer target type
main.c:558: warning: format â€˜%sâ€™ expects type â€˜char *â€™, but argument 4 has type â€˜const struct <anonymous> *â€™
main.c:565: warning: passing argument 2 of â€˜logdebugâ€™ from incompatible pointer type
main.c:566: warning: comparison between pointer and integer
main.c:566: warning: comparison between pointer and integer
main.c:569: warning: comparison between pointer and integer
main.c:569: warning: passing argument 1 of â€˜optslotâ€™ makes integer from pointer without a cast
main.c:569: error: â€˜struct <anonymous>â€™ has no member named â€˜has_argâ€™
main.c:570: warning: incompatible implicit declaration of built-in function â€˜fprintfâ€™
main.c:570: warning: passing argument 1 of â€˜optslotâ€™ makes integer from pointer without a cast
main.c:570: error: â€˜struct <anonymous>â€™ has no member named â€˜nameâ€™
main.c:570: warning: passing argument 1 of â€˜fprintfâ€™ discards qualifiers from pointer target type
main.c:570: warning: format â€˜%sâ€™ expects type â€˜char *â€™, but argument 4 has type â€˜const struct <anonymous> *â€™
main.c:572: warning: passing argument 1 of â€˜fprintfâ€™ discards qualifiers from pointer target type
main.c:572: warning: format â€˜%câ€™ expects type â€˜intâ€™, but argument 4 has type â€˜const struct <anonymous> *â€™
main.c:574: warning: implicit declaration of function â€˜strncmpâ€™
main.c:574: error: array subscript is not an integer
main.c:575: warning: incompatible implicit declaration of built-in function â€˜fprintfâ€™
main.c:575: error: array subscript is not an integer
main.c:575: warning: passing argument 1 of â€˜fprintfâ€™ discards qualifiers from pointer target type
main.c:575: warning: format â€˜%sâ€™ expects type â€˜char *â€™, but argument 4 has type â€˜const struct <anonymous> *â€™
main.c:578: warning: incompatible implicit declaration of built-in function â€˜fprintfâ€™
main.c:578: error: array subscript is not an integer
main.c:578: warning: passing argument 1 of â€˜fprintfâ€™ discards qualifiers from pointer target type
main.c:578: warning: format â€˜%sâ€™ expects type â€˜char *â€™, but argument 4 has type â€˜const struct <anonymous> *â€™
main.c:579: warning: passing argument 1 of â€˜fprintfâ€™ discards qualifiers from pointer target type
main.c:330: warning: unused variable â€˜optionsâ€™
main.c: In function â€˜setup_pin_timerâ€™:
main.c:601: error: storage size of â€˜ptyeventâ€™ isnâ€™t known
main.c:605: warning: implicit declaration of function â€˜memsetâ€™
main.c:605: warning: incompatible implicit declaration of built-in function â€˜memsetâ€™
main.c:605: warning: passing argument 3 of â€˜memsetâ€™ makes integer from pointer without a cast
main.c:608: error: request for member â€˜sigev_signoâ€™ in something not a structure or union
main.c:608: error: â€˜SIGRTMINâ€™ undeclared (first use in this function)
main.c:608: warning: statement with no effect
main.c:611: error: request for member â€˜sigev_notifyâ€™ in something not a structure or union
main.c:611: error: â€˜SIGEV_THREAD_IDâ€™ undeclared (first use in this function)
main.c:611: warning: statement with no effect
main.c:612: error: request for member â€˜_sigev_unâ€™ in something not a structure or union
main.c:612: error: request for member â€˜_tidâ€™ in something not a structure or union
main.c:612: warning: statement with no effect
main.c:614: warning: implicit declaration of function â€˜mtimer_createâ€™
main.c:614: error: â€˜CLOCK_REALTIMEâ€™ undeclared (first use in this function)
main.c:616: warning: passing argument 2 of â€˜logdebugâ€™ from incompatible pointer type
main.c:621: error: â€˜mtimer_tâ€™ has no member named â€˜idâ€™
main.c:621: warning: passing argument 1 of â€˜logwarnâ€™ from incompatible pointer type
main.c:622: warning: passing argument 2 of â€˜logsyserrorâ€™ from incompatible pointer type
main.c:625: warning: passing argument 3 of â€˜memsetâ€™ makes integer from pointer without a cast
main.c:628: error: request for member â€˜sigev_signoâ€™ in something not a structure or union
main.c:628: warning: statement with no effect
main.c:629: error: request for member â€˜sigev_notifyâ€™ in something not a structure or union
main.c:629: error: â€˜SIGEV_SIGNALâ€™ undeclared (first use in this function)
main.c:629: warning: statement with no effect
main.c:636: error: â€˜mtimer_tâ€™ has no member named â€˜idâ€™
main.c:636: warning: passing argument 1 of â€˜logerrâ€™ from incompatible pointer type
main.c:640: warning: passing argument 2 of â€˜logdebugâ€™ from incompatible pointer type
main.c:601: warning: unused variable â€˜ptyeventâ€™
main.c: At top level:
main.c:645: error: expected specifier-qualifier-list before â€˜uint8_tâ€™
main.c:658: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜io_uart_msrâ€™
main.c:659: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜io_uart_statusâ€™
main.c:663: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜dp_dsp_statusâ€™
main.c:664: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜dp_wDspRetrainStateâ€™
main.c: In function â€˜monitor_stateâ€™:
main.c:717: error: â€˜io_uart_msrâ€™ undeclared (first use in this function)
main.c:717: error: â€˜struct _stateâ€™ has no member named â€˜io_uart_msrâ€™
main.c:717: warning: implicit declaration of function â€˜sprintfâ€™
main.c:717: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:717: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:717: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:717: warning: implicit declaration of function â€˜__STRINGâ€™
main.c:717: error: expected â€˜)â€™ before string constant
main.c:717: warning: passing argument 2 of â€˜sprintfâ€™ makes pointer from integer without a cast
main.c:717: error: â€˜struct _stateâ€™ has no member named â€˜io_uart_msrâ€™
main.c:717: warning: statement with no effect
main.c:718: error: â€˜io_uart_statusâ€™ undeclared (first use in this function)
main.c:718: error: â€˜struct _stateâ€™ has no member named â€˜io_uart_statusâ€™
main.c:718: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:718: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:718: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:718: error: expected â€˜)â€™ before string constant
main.c:718: warning: passing argument 2 of â€˜sprintfâ€™ makes pointer from integer without a cast
main.c:718: error: â€˜struct _stateâ€™ has no member named â€˜io_uart_statusâ€™
main.c:718: warning: statement with no effect
main.c:719: error: â€˜struct _stateâ€™ has no member named â€˜x_modem_stateâ€™
main.c:719: warning: comparison between pointer and integer
main.c:719: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:719: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:719: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:719: error: expected â€˜)â€™ before string constant
main.c:719: warning: passing argument 2 of â€˜sprintfâ€™ makes pointer from integer without a cast
main.c:719: error: â€˜struct _stateâ€™ has no member named â€˜x_modem_stateâ€™
main.c:719: warning: statement with no effect
main.c:720: error: â€˜struct _stateâ€™ has no member named â€˜x_modem_modeâ€™
main.c:720: warning: comparison between pointer and integer
main.c:720: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:720: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:720: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:720: error: expected â€˜)â€™ before string constant
main.c:720: warning: passing argument 2 of â€˜sprintfâ€™ makes pointer from integer without a cast
main.c:720: error: â€˜struct _stateâ€™ has no member named â€˜x_modem_modeâ€™
main.c:720: warning: statement with no effect
main.c:721: error: â€˜struct _stateâ€™ has no member named â€˜x_line_rateâ€™
main.c:721: warning: comparison between pointer and integer
main.c:721: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:721: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:721: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:721: error: expected â€˜)â€™ before string constant
main.c:721: warning: passing argument 2 of â€˜sprintfâ€™ makes pointer from integer without a cast
main.c:721: error: â€˜struct _stateâ€™ has no member named â€˜x_line_rateâ€™
main.c:721: warning: statement with no effect
main.c:722: error: â€˜dp_dsp_statusâ€™ undeclared (first use in this function)
main.c:722: error: â€˜struct _stateâ€™ has no member named â€˜dp_dsp_statusâ€™
main.c:722: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:722: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:722: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:722: error: expected â€˜)â€™ before string constant
main.c:722: warning: passing argument 2 of â€˜sprintfâ€™ makes pointer from integer without a cast
main.c:722: error: â€˜struct _stateâ€™ has no member named â€˜dp_dsp_statusâ€™
main.c:722: warning: statement with no effect
main.c:723: error: â€˜struct _stateâ€™ has no member named â€˜io_app_tx_countâ€™
main.c:723: warning: comparison between pointer and integer
main.c:723: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:723: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:723: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:723: error: expected â€˜)â€™ before string constant
main.c:723: warning: passing argument 2 of â€˜sprintfâ€™ makes pointer from integer without a cast
main.c:723: error: â€˜struct _stateâ€™ has no member named â€˜io_app_tx_countâ€™
main.c:723: warning: statement with no effect
main.c:725: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:726: warning: passing argument 2 of â€˜logdebugâ€™ from incompatible pointer type
main.c:730: error: â€˜struct _stateâ€™ has no member named â€˜io_app_tx_bytesâ€™
main.c:730: warning: comparison between pointer and integer
main.c:730: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:730: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:730: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:730: error: â€˜io_app_txâ€™ undeclared (first use in this function)
main.c:730: error: expected â€˜)â€™ before string constant
main.c:730: warning: passing argument 2 of â€˜sprintfâ€™ makes pointer from integer without a cast
main.c:730: error: â€˜struct _stateâ€™ has no member named â€˜io_app_tx_bytesâ€™
main.c:730: warning: statement with no effect
main.c:731: error: â€˜struct _stateâ€™ has no member named â€˜io_dte_tx_bytesâ€™
main.c:731: warning: comparison between pointer and integer
main.c:731: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:731: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:731: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:731: error: â€˜io_dte_txâ€™ undeclared (first use in this function)
main.c:731: error: expected â€˜)â€™ before string constant
main.c:731: warning: passing argument 2 of â€˜sprintfâ€™ makes pointer from integer without a cast
main.c:731: error: â€˜struct _stateâ€™ has no member named â€˜io_dte_tx_bytesâ€™
main.c:731: warning: statement with no effect
main.c:732: error: â€˜struct _stateâ€™ has no member named â€˜io_dte_rx_bytesâ€™
main.c:732: warning: comparison between pointer and integer
main.c:732: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:732: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:732: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:732: error: â€˜io_dte_rxâ€™ undeclared (first use in this function)
main.c:732: error: expected â€˜)â€™ before string constant
main.c:732: warning: passing argument 2 of â€˜sprintfâ€™ makes pointer from integer without a cast
main.c:732: error: â€˜struct _stateâ€™ has no member named â€˜io_dte_rx_bytesâ€™
main.c:732: warning: statement with no effect
main.c:733: error: â€˜struct _stateâ€™ has no member named â€˜io_dce_tx_bytesâ€™
main.c:733: warning: comparison between pointer and integer
main.c:733: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:733: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:733: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:733: error: â€˜io_dce_txâ€™ undeclared (first use in this function)
main.c:733: error: expected â€˜)â€™ before string constant
main.c:733: warning: passing argument 2 of â€˜sprintfâ€™ makes pointer from integer without a cast
main.c:733: error: â€˜struct _stateâ€™ has no member named â€˜io_dce_tx_bytesâ€™
main.c:733: warning: statement with no effect
main.c:734: error: â€˜struct _stateâ€™ has no member named â€˜io_dce_rx_bytesâ€™
main.c:734: warning: comparison between pointer and integer
main.c:734: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:734: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:734: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:734: error: â€˜io_dce_rxâ€™ undeclared (first use in this function)
main.c:734: error: expected â€˜)â€™ before string constant
main.c:734: warning: passing argument 2 of â€˜sprintfâ€™ makes pointer from integer without a cast
main.c:734: error: â€˜struct _stateâ€™ has no member named â€˜io_dce_rx_bytesâ€™
main.c:734: warning: statement with no effect
main.c:736: warning: incompatible implicit declaration of built-in function â€˜sprintfâ€™
main.c:737: warning: passing argument 2 of â€˜logdebugâ€™ from incompatible pointer type
main.c: In function â€˜setup_pin_watcherâ€™:
main.c:758: error: storage size of â€˜timer_actionâ€™ isnâ€™t known
main.c:760: error: request for member â€˜sa_handlerâ€™ in something not a structure or union
main.c:760: warning: statement with no effect
main.c:761: error: request for member â€˜sa_flagsâ€™ in something not a structure or union
main.c:761: warning: statement with no effect
main.c:762: warning: implicit declaration of function â€˜sigemptysetâ€™
main.c:762: error: request for member â€˜sa_maskâ€™ in something not a structure or union
main.c:763: warning: implicit declaration of function â€˜sigactionâ€™
main.c:763: error: â€˜SIGRTMINâ€™ undeclared (first use in this function)
main.c:758: warning: unused variable â€˜timer_actionâ€™
main.c:766:19: error: errno.h: No such file or directory
main.c: At top level:
main.c:769: error: expected â€˜)â€™ before â€˜*â€™ token
main.c: In function â€˜mainâ€™:
main.c:837: error: â€˜struct _configâ€™ has no member named â€˜syslogâ€™
main.c:840: error: â€˜struct _configâ€™ has no member named â€˜daemonâ€™
main.c:841: warning: implicit declaration of function â€˜daemonâ€™
main.c:841: error: â€˜struct _configâ€™ has no member named â€˜logfileâ€™
main.c:843: warning: passing argument 2 of â€˜logsyserrorâ€™ from incompatible pointer type
main.c:844: warning: passing argument 1 of â€˜logwarnâ€™ from incompatible pointer type
main.c:845: error: â€˜struct _configâ€™ has no member named â€˜daemonâ€™
main.c:845: warning: statement with no effect
main.c:848: error: â€˜struct _configâ€™ has no member named â€˜daemonâ€™
main.c:848: error: â€˜struct _configâ€™ has no member named â€˜logfileâ€™
main.c:849: error: â€˜struct _configâ€™ has no member named â€˜syslogâ€™
main.c:849: warning: statement with no effect
main.c:852: warning: passing argument 2 of â€˜logdebugâ€™ from incompatible pointer type
main.c:862: warning: passing argument 2 of â€˜logdebugâ€™ from incompatible pointer type
main.c:871: warning: implicit declaration of function â€˜snprintfâ€™
main.c:871: warning: incompatible implicit declaration of built-in function â€˜snprintfâ€™
main.c:874: warning: incompatible implicit declaration of built-in function â€˜snprintfâ€™
main.c:878: warning: incompatible implicit declaration of built-in function â€˜snprintfâ€™
main.c:880: warning: implicit declaration of function â€˜strlenâ€™
main.c:880: warning: incompatible implicit declaration of built-in function â€˜strlenâ€™
main.c:885: warning: passing argument 2 of â€˜logdebugâ€™ from incompatible pointer type
main.c:888: error: â€˜struct _configâ€™ has no member named â€˜misrâ€™
main.c:888: error: incompatible type for argument 1 of â€˜misr_strâ€™
main.c:888: error: â€˜struct _configâ€™ has no member named â€˜realtimeâ€™
main.c:888: warning: passing argument 2 of â€˜logdebugâ€™ from incompatible pointer type
main.c:909: warning: passing argument 2 of â€˜mthread_createâ€™ discards qualifiers from pointer target type
main.c:910: warning: passing argument 1 of â€˜logerrâ€™ from incompatible pointer type
main.c:913: warning: passing argument 2 of â€˜logdebugâ€™ from incompatible pointer type
main.c:924: warning: passing argument 1 of â€˜loginfoâ€™ from incompatible pointer type
main.c:928: warning: passing argument 2 of â€˜logdebugâ€™ from incompatible pointer type
main.c:933: warning: implicit declaration of function â€˜mkfifoâ€™
main.c:934: error: â€˜errnoâ€™ undeclared (first use in this function)
main.c:934: error: â€˜EEXISTâ€™ undeclared (first use in this function)
main.c:935: warning: passing argument 2 of â€˜logdebugâ€™ from incompatible pointer type
main.c:937: warning: passing argument 2 of â€˜logsyserrorâ€™ from incompatible pointer type
main.c:940: error: â€˜FILEâ€™ undeclared (first use in this function)
main.c:940: error: â€˜controlâ€™ undeclared (first use in this function)
main.c:940: error: invalid operands to binary *
main.c:940: warning: statement with no effect
main.c:943: warning: implicit declaration of function â€˜fopenâ€™
main.c:943: warning: statement with no effect
main.c:944: error: â€˜EINTRâ€™ undeclared (first use in this function)
main.c:950: warning: passing argument 2 of â€˜logsyserrorâ€™ from incompatible pointer type
main.c:951: warning: passing argument 1 of â€˜logwarnâ€™ from incompatible pointer type
main.c:958: warning: implicit declaration of function â€˜get_cmdâ€™
main.c:961: warning: passing argument 2 of â€˜logdebugâ€™ from incompatible pointer type
main.c:962: warning: implicit declaration of function â€˜fcloseâ€™
main.c:964: warning: statement with no effect
main.c:971: warning: passing argument 2 of â€˜logsyserrorâ€™ from incompatible pointer type
main.c:972: warning: passing argument 1 of â€˜logwarnâ€™ from incompatible pointer type
main.c:978: warning: passing argument 1 of â€˜loginfoâ€™ from incompatible pointer type
main.c:984: error: â€˜__u32â€™ undeclared (first use in this function)
main.c:984: error: expected expression before â€˜)â€™ token
main.c:984: error: invalid operands to binary *
main.c:984: error: called object â€˜<erroneous-expression>â€™ is not a function
main.c:984: error: assignment of read-only location
main.c:984: error: incompatible types in assignment
main.c:984: warning: statement with no effect
main.c:985: error: â€˜__u16â€™ undeclared (first use in this function)
main.c:985: error: expected expression before â€˜)â€™ token
main.c:985: error: invalid operands to binary *
main.c:985: error: called object â€˜<erroneous-expression>â€™ is not a function
main.c:985: error: assignment of read-only location
main.c:985: error: incompatible types in assignment
main.c:985: warning: statement with no effect
main.c:992: warning: passing argument 1 of â€˜loginfoâ€™ from incompatible pointer type
main.c:993: warning: implicit declaration of function â€˜ioctlâ€™
main.c:993: warning: implicit declaration of function â€˜_IOâ€™
main.c:995: warning: passing argument 2 of â€˜logsyserrorâ€™ from incompatible pointer type
main.c:999: warning: passing argument 1 of â€˜loginfoâ€™ from incompatible pointer type
main.c:1002: warning: passing argument 2 of â€˜logsyserrorâ€™ from incompatible pointer type
main.c:1005: warning: passing argument 2 of â€˜logdebugâ€™ from incompatible pointer type
main.c:1013: warning: implicit declaration of function â€˜pauseâ€™
main.c: In function â€˜serve_portâ€™:
main.c:1029: warning: passing argument 2 of â€˜logdebugâ€™ from incompatible pointer type
main.c:1031: error: â€˜struct _configâ€™ has no member named â€˜realtimeâ€™
main.c:1041: warning: passing argument 1 of â€˜logerrâ€™ from incompatible pointer type
main.c:1042: warning: incompatible implicit declaration of built-in function â€˜exitâ€™
main.c:1047: warning: passing argument 1 of â€˜logerrâ€™ from incompatible pointer type
main.c:1050: warning: passing argument 2 of â€˜logdebugâ€™ from incompatible pointer type
main.c:1055: warning: passing argument 2 of â€˜logdebugâ€™ from incompatible pointer type
main.c: In function â€˜mexitâ€™:
main.c:1082: error: â€˜struct _configâ€™ has no member named â€˜daemonâ€™
main.c:1083: warning: passing argument 1 of â€˜loginfoâ€™ from incompatible pointer type
main.c:1085: warning: passing argument 1 of â€˜loginfoâ€™ from incompatible pointer type
main.c:1086: warning: incompatible implicit declaration of built-in function â€˜exitâ€™
main.c: In function â€˜kbdint_handlerâ€™:
main.c:1093: warning: passing argument 2 of â€˜logdebugâ€™ from incompatible pointer type
main.c: In function â€˜setup_kbd_interruptâ€™:
main.c:1098: error: storage size of â€˜timer_actionâ€™ isnâ€™t known
main.c:1100: error: request for member â€˜sa_handlerâ€™ in something not a structure or union
main.c:1100: warning: statement with no effect
main.c:1101: error: request for member â€˜sa_flagsâ€™ in something not a structure or union
main.c:1101: warning: statement with no effect
main.c:1102: error: request for member â€˜sa_maskâ€™ in something not a structure or union
main.c:1103: error: â€˜SIGINTâ€™ undeclared (first use in this function)
main.c:1098: warning: unused variable â€˜timer_actionâ€™
main.c: In function â€˜sigterm_handlerâ€™:
main.c:1107: warning: passing argument 2 of â€˜logdebugâ€™ from incompatible pointer type
main.c: In function â€˜setup_daemon_signalsâ€™:
main.c:1112: error: storage size of â€˜timer_actionâ€™ isnâ€™t known
main.c:1114: error: request for member â€˜sa_handlerâ€™ in something not a structure or union
main.c:1114: warning: statement with no effect
main.c:1115: error: request for member â€˜sa_flagsâ€™ in something not a structure or union
main.c:1115: warning: statement with no effect
main.c:1116: error: request for member â€˜sa_maskâ€™ in something not a structure or union
main.c:1117: error: â€˜SIGTERMâ€™ undeclared (first use in this function)
main.c:1112: warning: unused variable â€˜timer_actionâ€™
main.c: In function â€˜setup_segvâ€™:
main.c:1124: error: storage size of â€˜actionâ€™ isnâ€™t known
main.c:1126: error: request for member â€˜sa_handlerâ€™ in something not a structure or union
main.c:1126: warning: statement with no effect
main.c:1127: error: request for member â€˜sa_flagsâ€™ in something not a structure or union
main.c:1127: warning: statement with no effect
main.c:1128: error: request for member â€˜sa_maskâ€™ in something not a structure or union
main.c:1129: error: â€˜SIGSEGVâ€™ undeclared (first use in this function)
main.c:1124: warning: unused variable â€˜actionâ€™
main.c: In function â€˜segv_handlerâ€™:
main.c:1133: error: storage size of â€˜actionâ€™ isnâ€™t known
main.c:1136: warning: incompatible implicit declaration of built-in function â€˜printfâ€™
main.c:1138: error: request for member â€˜sa_handlerâ€™ in something not a structure or union
main.c:1138: error: â€˜SIG_DFLâ€™ undeclared (first use in this function)
main.c:1138: warning: statement with no effect
main.c:1139: error: request for member â€˜sa_flagsâ€™ in something not a structure or union
main.c:1139: warning: statement with no effect
main.c:1140: error: request for member â€˜sa_maskâ€™ in something not a structure or union
main.c:1141: error: â€˜SIGSEGVâ€™ undeclared (first use in this function)
main.c:1133: warning: unused variable â€˜actionâ€™
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/home/teriwood/Desktop/martain/modem'
make: *** [install] Error 2
teriwood@teriwood-desktop:~/Desktop/martain$ 

 
```

Thanks again.

Teri

---

