---
title: "Still having trouble with Dial-up/Lucent modem install"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by teriwood on 2008-04-09
Hello --

Firstly, my thanks for the help on the other thread, but I'm still stalling out on the installation.  I suspect that it probably boils down to a mistake in my logic.  But as I've never done anything like this before, I can't figure it out.

So I've decided just to post exactly what I'm doing, and hopefully someone will instantly see where I'm going astray in my thinking.

I have the instruction page that everyone points you too.  I have martian-full-20071011, and also downloaded ltmdmobj.o-8.31-gcc3 and ltmdmobj.o-8.31-gcc4.

I type: **cd [COLOR="DarkOliveGreen"]Desktop/martian[/COLOR]** to get to that directory. I type and enter: **[COLOR="DarkOliveGreen"]lls[/COLOR]** and the terminal gives me exactly what's listed on the instruction page. So good so far.

The instruction pages says that I must copy the two ltmdmobj.o files 3 and 4 into my martain/modem folder. So I extract them there. I should note that the original martain-full does have a ltmdmobj.o file already. I am hoping this is not a problem.

I type the next command: **[COLOR="DarkOliveGreen"]make clean[/COLOR]**. Again, I get the exact result in the terminal window that the instruction pages says I should. So again, so far so good.

But after this, it goes haywire. I type the next command: **[COLOR="DarkOliveGreen"]make[/COLOR]** - and get errors.

This is what my terminal says at this point.  :confused:

```
main.c:530: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type
main.c:533: warning: implicit declaration of function ‘printf’
main.c:533: warning: incompatible implicit declaration of built-in function ‘printf’
main.c:538: warning: passing argument 1 of ‘logwarn’ from incompatible pointer type
main.c:541: warning: incompatible implicit declaration of built-in function ‘exit’
main.c:544: error: ‘optind’ undeclared (first use in this function)
main.c:544: warning: comparison between pointer and integer
main.c:545: error: array subscript is not an integer
main.c:545: warning: assignment from incompatible pointer type
main.c:547: warning: comparison between pointer and integer
main.c:548: warning: passing argument 1 of ‘logwarn’ from incompatible pointer type
main.c:554: warning: comparison between pointer and integer
main.c:554: warning: comparison between pointer and integer
main.c:556: error: ‘optopt’ undeclared (first use in this function)
main.c:557: warning: comparison between pointer and integer
main.c:557: warning: passing argument 1 of ‘optslot’ makes integer from pointer without a cast
main.c:557: error: ‘struct <anonymous>’ has no member named ‘has_arg’
main.c:558: warning: incompatible implicit declaration of built-in function ‘fprintf’
main.c:558: warning: passing argument 1 of ‘optslot’ makes integer from pointer without a cast
main.c:558: error: ‘struct <anonymous>’ has no member named ‘name’
main.c:558: warning: passing argument 1 of ‘fprintf’ discards qualifiers from pointer target type
main.c:558: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘const struct <anonymous> *’
main.c:565: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type
main.c:566: warning: comparison between pointer and integer
main.c:566: warning: comparison between pointer and integer
main.c:569: warning: comparison between pointer and integer
main.c:569: warning: passing argument 1 of ‘optslot’ makes integer from pointer without a cast
main.c:569: error: ‘struct <anonymous>’ has no member named ‘has_arg’
main.c:570: warning: incompatible implicit declaration of built-in function ‘fprintf’
main.c:570: warning: passing argument 1 of ‘optslot’ makes integer from pointer without a cast
main.c:570: error: ‘struct <anonymous>’ has no member named ‘name’
main.c:570: warning: passing argument 1 of ‘fprintf’ discards qualifiers from pointer target type
main.c:570: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘const struct <anonymous> *’
main.c:572: warning: passing argument 1 of ‘fprintf’ discards qualifiers from pointer target type
main.c:572: warning: format ‘%c’ expects type ‘int’, but argument 4 has type ‘const struct <anonymous> *’
main.c:574: warning: implicit declaration of function ‘strncmp’
main.c:574: error: array subscript is not an integer
main.c:575: warning: incompatible implicit declaration of built-in function ‘fprintf’
main.c:575: error: array subscript is not an integer
main.c:575: warning: passing argument 1 of ‘fprintf’ discards qualifiers from pointer target type
main.c:575: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘const struct <anonymous> *’
main.c:578: warning: incompatible implicit declaration of built-in function ‘fprintf’
main.c:578: error: array subscript is not an integer
main.c:578: warning: passing argument 1 of ‘fprintf’ discards qualifiers from pointer target type
main.c:578: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘const struct <anonymous> *’
main.c:579: warning: passing argument 1 of ‘fprintf’ discards qualifiers from pointer target type
main.c:330: warning: unused variable ‘options’
main.c: In function ‘setup_pin_timer’:
main.c:601: error: storage size of ‘ptyevent’ isn’t known
main.c:605: warning: implicit declaration of function ‘memset’
main.c:605: warning: incompatible implicit declaration of built-in function ‘memset’
main.c:605: warning: passing argument 3 of ‘memset’ makes integer from pointer without a cast
main.c:608: error: request for member ‘sigev_signo’ in something not a structure or union
main.c:608: error: ‘SIGRTMIN’ undeclared (first use in this function)
main.c:608: warning: statement with no effect
main.c:611: error: request for member ‘sigev_notify’ in something not a structure or union
main.c:611: error: ‘SIGEV_THREAD_ID’ undeclared (first use in this function)
main.c:611: warning: statement with no effect
main.c:612: error: request for member ‘_sigev_un’ in something not a structure or union
main.c:612: error: request for member ‘_tid’ in something not a structure or union
main.c:612: warning: statement with no effect
main.c:614: warning: implicit declaration of function ‘mtimer_create’
main.c:614: error: ‘CLOCK_REALTIME’ undeclared (first use in this function)
main.c:616: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type
main.c:621: error: ‘mtimer_t’ has no member named ‘id’
main.c:621: warning: passing argument 1 of ‘logwarn’ from incompatible pointer type
main.c:622: warning: passing argument 2 of ‘logsyserror’ from incompatible pointer type
main.c:625: warning: passing argument 3 of ‘memset’ makes integer from pointer without a cast
main.c:628: error: request for member ‘sigev_signo’ in something not a structure or union
main.c:628: warning: statement with no effect
main.c:629: error: request for member ‘sigev_notify’ in something not a structure or union
main.c:629: error: ‘SIGEV_SIGNAL’ undeclared (first use in this function)
main.c:629: warning: statement with no effect
main.c:636: error: ‘mtimer_t’ has no member named ‘id’
main.c:636: warning: passing argument 1 of ‘logerr’ from incompatible pointer type
main.c:640: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type
main.c:601: warning: unused variable ‘ptyevent’
main.c: At top level:
main.c:645: error: expected specifier-qualifier-list before ‘uint8_t’
main.c:658: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘io_uart_msr’
main.c:659: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘io_uart_status’
main.c:663: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘dp_dsp_status’
main.c:664: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘dp_wDspRetrainState’
main.c: In function ‘monitor_state’:
main.c:717: error: ‘io_uart_msr’ undeclared (first use in this function)
main.c:717: error: ‘struct _state’ has no member named ‘io_uart_msr’
main.c:717: warning: implicit declaration of function ‘sprintf’
main.c:717: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:717: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:717: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:717: warning: implicit declaration of function ‘__STRING’
main.c:717: error: expected ‘)’ before string constant
main.c:717: warning: passing argument 2 of ‘sprintf’ makes pointer from integer without a cast
main.c:717: error: ‘struct _state’ has no member named ‘io_uart_msr’
main.c:717: warning: statement with no effect
main.c:718: error: ‘io_uart_status’ undeclared (first use in this function)
main.c:718: error: ‘struct _state’ has no member named ‘io_uart_status’
main.c:718: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:718: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:718: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:718: error: expected ‘)’ before string constant
main.c:718: warning: passing argument 2 of ‘sprintf’ makes pointer from integer without a cast
main.c:718: error: ‘struct _state’ has no member named ‘io_uart_status’
main.c:718: warning: statement with no effect
main.c:719: error: ‘struct _state’ has no member named ‘x_modem_state’
main.c:719: warning: comparison between pointer and integer
main.c:719: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:719: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:719: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:719: error: expected ‘)’ before string constant
main.c:719: warning: passing argument 2 of ‘sprintf’ makes pointer from integer without a cast
main.c:719: error: ‘struct _state’ has no member named ‘x_modem_state’
main.c:719: warning: statement with no effect
main.c:720: error: ‘struct _state’ has no member named ‘x_modem_mode’
main.c:720: warning: comparison between pointer and integer
main.c:720: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:720: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:720: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:720: error: expected ‘)’ before string constant
main.c:720: warning: passing argument 2 of ‘sprintf’ makes pointer from integer without a cast
main.c:720: error: ‘struct _state’ has no member named ‘x_modem_mode’
main.c:720: warning: statement with no effect
main.c:721: error: ‘struct _state’ has no member named ‘x_line_rate’
main.c:721: warning: comparison between pointer and integer
main.c:721: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:721: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:721: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:721: error: expected ‘)’ before string constant
main.c:721: warning: passing argument 2 of ‘sprintf’ makes pointer from integer without a cast
main.c:721: error: ‘struct _state’ has no member named ‘x_line_rate’
main.c:721: warning: statement with no effect
main.c:722: error: ‘dp_dsp_status’ undeclared (first use in this function)
main.c:722: error: ‘struct _state’ has no member named ‘dp_dsp_status’
main.c:722: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:722: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:722: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:722: error: expected ‘)’ before string constant
main.c:722: warning: passing argument 2 of ‘sprintf’ makes pointer from integer without a cast
main.c:722: error: ‘struct _state’ has no member named ‘dp_dsp_status’
main.c:722: warning: statement with no effect
main.c:723: error: ‘struct _state’ has no member named ‘io_app_tx_count’
main.c:723: warning: comparison between pointer and integer
main.c:723: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:723: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:723: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:723: error: expected ‘)’ before string constant
main.c:723: warning: passing argument 2 of ‘sprintf’ makes pointer from integer without a cast
main.c:723: error: ‘struct _state’ has no member named ‘io_app_tx_count’
main.c:723: warning: statement with no effect
main.c:725: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:726: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type
main.c:730: error: ‘struct _state’ has no member named ‘io_app_tx_bytes’
main.c:730: warning: comparison between pointer and integer
main.c:730: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:730: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:730: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:730: error: ‘io_app_tx’ undeclared (first use in this function)
main.c:730: error: expected ‘)’ before string constant
main.c:730: warning: passing argument 2 of ‘sprintf’ makes pointer from integer without a cast
main.c:730: error: ‘struct _state’ has no member named ‘io_app_tx_bytes’
main.c:730: warning: statement with no effect
main.c:731: error: ‘struct _state’ has no member named ‘io_dte_tx_bytes’
main.c:731: warning: comparison between pointer and integer
main.c:731: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:731: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:731: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:731: error: ‘io_dte_tx’ undeclared (first use in this function)
main.c:731: error: expected ‘)’ before string constant
main.c:731: warning: passing argument 2 of ‘sprintf’ makes pointer from integer without a cast
main.c:731: error: ‘struct _state’ has no member named ‘io_dte_tx_bytes’
main.c:731: warning: statement with no effect
main.c:732: error: ‘struct _state’ has no member named ‘io_dte_rx_bytes’
main.c:732: warning: comparison between pointer and integer
main.c:732: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:732: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:732: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:732: error: ‘io_dte_rx’ undeclared (first use in this function)
main.c:732: error: expected ‘)’ before string constant
main.c:732: warning: passing argument 2 of ‘sprintf’ makes pointer from integer without a cast
main.c:732: error: ‘struct _state’ has no member named ‘io_dte_rx_bytes’
main.c:732: warning: statement with no effect
main.c:733: error: ‘struct _state’ has no member named ‘io_dce_tx_bytes’
main.c:733: warning: comparison between pointer and integer
main.c:733: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:733: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:733: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:733: error: ‘io_dce_tx’ undeclared (first use in this function)
main.c:733: error: expected ‘)’ before string constant
main.c:733: warning: passing argument 2 of ‘sprintf’ makes pointer from integer without a cast
main.c:733: error: ‘struct _state’ has no member named ‘io_dce_tx_bytes’
main.c:733: warning: statement with no effect
main.c:734: error: ‘struct _state’ has no member named ‘io_dce_rx_bytes’
main.c:734: warning: comparison between pointer and integer
main.c:734: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:734: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:734: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:734: error: ‘io_dce_rx’ undeclared (first use in this function)
main.c:734: error: expected ‘)’ before string constant
main.c:734: warning: passing argument 2 of ‘sprintf’ makes pointer from integer without a cast
main.c:734: error: ‘struct _state’ has no member named ‘io_dce_rx_bytes’
main.c:734: warning: statement with no effect
main.c:736: warning: incompatible implicit declaration of built-in function ‘sprintf’
main.c:737: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type
main.c: In function ‘setup_pin_watcher’:
main.c:758: error: storage size of ‘timer_action’ isn’t known
main.c:760: error: request for member ‘sa_handler’ in something not a structure or union
main.c:760: warning: statement with no effect
main.c:761: error: request for member ‘sa_flags’ in something not a structure or union
main.c:761: warning: statement with no effect
main.c:762: warning: implicit declaration of function ‘sigemptyset’
main.c:762: error: request for member ‘sa_mask’ in something not a structure or union
main.c:763: warning: implicit declaration of function ‘sigaction’
main.c:763: error: ‘SIGRTMIN’ undeclared (first use in this function)
main.c:758: warning: unused variable ‘timer_action’
main.c:766:19: error: errno.h: No such file or directory
main.c: At top level:
main.c:769: error: expected ‘)’ before ‘*’ token
main.c: In function ‘main’:
main.c:837: error: ‘struct _config’ has no member named ‘syslog’
main.c:840: error: ‘struct _config’ has no member named ‘daemon’
main.c:841: warning: implicit declaration of function ‘daemon’
main.c:841: error: ‘struct _config’ has no member named ‘logfile’
main.c:843: warning: passing argument 2 of ‘logsyserror’ from incompatible pointer type
main.c:844: warning: passing argument 1 of ‘logwarn’ from incompatible pointer type
main.c:845: error: ‘struct _config’ has no member named ‘daemon’
main.c:845: warning: statement with no effect
main.c:848: error: ‘struct _config’ has no member named ‘daemon’
main.c:848: error: ‘struct _config’ has no member named ‘logfile’
main.c:849: error: ‘struct _config’ has no member named ‘syslog’
main.c:849: warning: statement with no effect
main.c:852: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type
main.c:862: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type
main.c:871: warning: implicit declaration of function ‘snprintf’
main.c:871: warning: incompatible implicit declaration of built-in function ‘snprintf’
main.c:874: warning: incompatible implicit declaration of built-in function ‘snprintf’
main.c:878: warning: incompatible implicit declaration of built-in function ‘snprintf’
main.c:880: warning: implicit declaration of function ‘strlen’
main.c:880: warning: incompatible implicit declaration of built-in function ‘strlen’
main.c:885: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type
main.c:888: error: ‘struct _config’ has no member named ‘misr’
main.c:888: error: incompatible type for argument 1 of ‘misr_str’
main.c:888: error: ‘struct _config’ has no member named ‘realtime’
main.c:888: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type
main.c:909: warning: passing argument 2 of ‘mthread_create’ discards qualifiers from pointer target type
main.c:910: warning: passing argument 1 of ‘logerr’ from incompatible pointer type
main.c:913: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type
main.c:924: warning: passing argument 1 of ‘loginfo’ from incompatible pointer type
main.c:928: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type
main.c:933: warning: implicit declaration of function ‘mkfifo’
main.c:934: error: ‘errno’ undeclared (first use in this function)
main.c:934: error: ‘EEXIST’ undeclared (first use in this function)
main.c:935: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type
main.c:937: warning: passing argument 2 of ‘logsyserror’ from incompatible pointer type
main.c:940: error: ‘FILE’ undeclared (first use in this function)
main.c:940: error: ‘control’ undeclared (first use in this function)
main.c:940: error: invalid operands to binary *
main.c:940: warning: statement with no effect
main.c:943: warning: implicit declaration of function ‘fopen’
main.c:943: warning: statement with no effect
main.c:944: error: ‘EINTR’ undeclared (first use in this function)
main.c:950: warning: passing argument 2 of ‘logsyserror’ from incompatible pointer type
main.c:951: warning: passing argument 1 of ‘logwarn’ from incompatible pointer type
main.c:958: warning: implicit declaration of function ‘get_cmd’
main.c:961: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type
main.c:962: warning: implicit declaration of function ‘fclose’
main.c:964: warning: statement with no effect
main.c:971: warning: passing argument 2 of ‘logsyserror’ from incompatible pointer type
main.c:972: warning: passing argument 1 of ‘logwarn’ from incompatible pointer type
main.c:978: warning: passing argument 1 of ‘loginfo’ from incompatible pointer type
main.c:984: error: ‘__u32’ undeclared (first use in this function)
main.c:984: error: expected expression before ‘)’ token
main.c:984: error: invalid operands to binary *
main.c:984: error: called object ‘<erroneous-expression>’ is not a function
main.c:984: error: assignment of read-only location
main.c:984: error: incompatible types in assignment
main.c:984: warning: statement with no effect
main.c:985: error: ‘__u16’ undeclared (first use in this function)
main.c:985: error: expected expression before ‘)’ token
main.c:985: error: invalid operands to binary *
main.c:985: error: called object ‘<erroneous-expression>’ is not a function
main.c:985: error: assignment of read-only location
main.c:985: error: incompatible types in assignment
main.c:985: warning: statement with no effect
main.c:992: warning: passing argument 1 of ‘loginfo’ from incompatible pointer type
main.c:993: warning: implicit declaration of function ‘ioctl’
main.c:993: warning: implicit declaration of function ‘_IO’
main.c:995: warning: passing argument 2 of ‘logsyserror’ from incompatible pointer type
main.c:999: warning: passing argument 1 of ‘loginfo’ from incompatible pointer type
main.c:1002: warning: passing argument 2 of ‘logsyserror’ from incompatible pointer type
main.c:1005: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type
main.c:1013: warning: implicit declaration of function ‘pause’
main.c: In function ‘serve_port’:
main.c:1029: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type
main.c:1031: error: ‘struct _config’ has no member named ‘realtime’
main.c:1041: warning: passing argument 1 of ‘logerr’ from incompatible pointer type
main.c:1042: warning: incompatible implicit declaration of built-in function ‘exit’
main.c:1047: warning: passing argument 1 of ‘logerr’ from incompatible pointer type
main.c:1050: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type
main.c:1055: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type
main.c: In function ‘mexit’:
main.c:1082: error: ‘struct _config’ has no member named ‘daemon’
main.c:1083: warning: passing argument 1 of ‘loginfo’ from incompatible pointer type
main.c:1085: warning: passing argument 1 of ‘loginfo’ from incompatible pointer type
main.c:1086: warning: incompatible implicit declaration of built-in function ‘exit’
main.c: In function ‘kbdint_handler’:
main.c:1093: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type
main.c: In function ‘setup_kbd_interrupt’:
main.c:1098: error: storage size of ‘timer_action’ isn’t known
main.c:1100: error: request for member ‘sa_handler’ in something not a structure or union
main.c:1100: warning: statement with no effect
main.c:1101: error: request for member ‘sa_flags’ in something not a structure or union
main.c:1101: warning: statement with no effect
main.c:1102: error: request for member ‘sa_mask’ in something not a structure or union
main.c:1103: error: ‘SIGINT’ undeclared (first use in this function)
main.c:1098: warning: unused variable ‘timer_action’
main.c: In function ‘sigterm_handler’:
main.c:1107: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type
main.c: In function ‘setup_daemon_signals’:
main.c:1112: error: storage size of ‘timer_action’ isn’t known
main.c:1114: error: request for member ‘sa_handler’ in something not a structure or union
main.c:1114: warning: statement with no effect
main.c:1115: error: request for member ‘sa_flags’ in something not a structure or union
main.c:1115: warning: statement with no effect
main.c:1116: error: request for member ‘sa_mask’ in something not a structure or union
main.c:1117: error: ‘SIGTERM’ undeclared (first use in this function)
main.c:1112: warning: unused variable ‘timer_action’
main.c: In function ‘setup_segv’:
main.c:1124: error: storage size of ‘action’ isn’t known
main.c:1126: error: request for member ‘sa_handler’ in something not a structure or union
main.c:1126: warning: statement with no effect
main.c:1127: error: request for member ‘sa_flags’ in something not a structure or union
main.c:1127: warning: statement with no effect
main.c:1128: error: request for member ‘sa_mask’ in something not a structure or union
main.c:1129: error: ‘SIGSEGV’ undeclared (first use in this function)
main.c:1124: warning: unused variable ‘action’
main.c: In function ‘segv_handler’:
main.c:1133: error: storage size of ‘action’ isn’t known
main.c:1136: warning: incompatible implicit declaration of built-in function ‘printf’
main.c:1138: error: request for member ‘sa_handler’ in something not a structure or union
main.c:1138: error: ‘SIG_DFL’ undeclared (first use in this function)
main.c:1138: warning: statement with no effect
main.c:1139: error: request for member ‘sa_flags’ in something not a structure or union
main.c:1139: warning: statement with no effect
main.c:1140: error: request for member ‘sa_mask’ in something not a structure or union
main.c:1141: error: ‘SIGSEGV’ undeclared (first use in this function)
main.c:1133: warning: unused variable ‘action’
```

(sighs)  One wonders if I'm smart enough for this -- but I'm determined to figure this out.  I really do want to rise above Windows finally ...

All my thanks again, for your time and your trouble.

---

### Post by stchman on 2008-04-09
Thing is that Linux has very poor support for Winmodems and Lucent is famous for Winmodems.  If you need dialup I recommend getting a PCI HARDWARE modem.  That kind of modem will work out of the box.

Here is a good modem for Linux and the person talks about it running on Ubuntu.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16825134002](http://www.newegg.com/Product/Product.aspx?Item=N82E16825134002)

---

### Post by Shazaam on 2008-04-09
It looks like (from the instructions) you are running too many make commands. During a compile the usual commands are these....
```
./configure
make
sudo make install
```
So after the "make clean" you would enter the "sudo make install" command.

---

### Post by RJQ on 2008-05-23
The last post is right, also if you are runing Hardy you will need martian-full-20080407, I just make a [tutorial]("http://ubuntuforums.org/showthread.php?t=804378") for this modem if you want to try it, I have been using it for almost a year now and with no problems at all, if you know you have the lucent agere modem I am sure it will work.
cheers!

---

