---
title: "Problems Compiling and Installing"
date: 2012-06-17
forum: Any Other OS
---

### Post by Kabuku on 2012-06-17
I'm actually using BackTrack 5 but since new threads have to be approved by moderators over there and the forums aren't that active anyway and since I've heard that Backtrack is basicly Ubuntu... Here I am!

I'm trying to compile and install symbion sslproxy and linsql. With both, there seem to be errors occurring in the make/compile process. And then, obviously there is no executable or whatever you call it.

This is what I get when I run make from the commandline for Symbion
```
root@root:/sslproxy-1.1.2# make
gcc -c -Wall -g3 -DVERSION=\"1.1.2\"   ssl_proxy.c -o ssl_proxy.o
ssl_proxy.c:45:25: error: openssl/ssl.h: No such file or directory
ssl_proxy.c:46:25: error: openssl/err.h: No such file or directory
ssl_proxy.c:47:26: error: openssl/x509.h: No such file or directory
ssl_proxy.c:48:25: error: openssl/pem.h: No such file or directory
ssl_proxy.c:49:28: error: openssl/crypto.h: No such file or directory
ssl_proxy.c:50:26: error: openssl/rand.h: No such file or directory
ssl_proxy.c:67: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
ssl_proxy.c:83: error: expected specifier-qualifier-list before &#8216;SSL&#8217;
ssl_proxy.c: In function &#8216;server_init&#8217;:
ssl_proxy.c:133: warning: implicit declaration of function &#8216;exit&#8217;
ssl_proxy.c:133: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
ssl_proxy.c:142: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
ssl_proxy.c: At top level:
ssl_proxy.c:162: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
ssl_proxy.c:173: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;X509_STORE_CTX&#8217;
ssl_proxy.c: In function &#8216;server_ssl_init&#8217;:
ssl_proxy.c:181: warning: implicit declaration of function &#8216;SSLeay_add_ssl_algorithms&#8217;
ssl_proxy.c:182: warning: implicit declaration of function &#8216;SSL_load_error_strings&#8217;
ssl_proxy.c:183: error: &#8216;server_ssl_ctx&#8217; undeclared (first use in this function)
ssl_proxy.c:183: error: (Each undeclared identifier is reported only once
ssl_proxy.c:183: error: for each function it appears in.)
ssl_proxy.c:183: warning: implicit declaration of function &#8216;SSL_CTX_new&#8217;
ssl_proxy.c:183: warning: implicit declaration of function &#8216;SSLv23_server_method&#8217;
ssl_proxy.c:184: warning: implicit declaration of function &#8216;SSL_CTX_set_cipher_list&#8217;
ssl_proxy.c:185: warning: implicit declaration of function &#8216;SSL_CTX_set_default_verify_paths&#8217;
ssl_proxy.c:187: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
ssl_proxy.c:190: warning: implicit declaration of function &#8216;SSL_CTX_use_certificate_chain_file&#8217;
ssl_proxy.c:192: warning: implicit declaration of function &#8216;ERR_error_string&#8217;
ssl_proxy.c:192: warning: implicit declaration of function &#8216;ERR_get_error&#8217;
ssl_proxy.c:192: warning: format &#8216;%.256s&#8217; expects type &#8216;char *&#8217;, but argument 3 has type &#8216;int&#8217;
ssl_proxy.c:193: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
ssl_proxy.c:195: warning: implicit declaration of function &#8216;SSL_CTX_use_PrivateKey_file&#8217;
ssl_proxy.c:195: error: &#8216;SSL_FILETYPE_PEM&#8217; undeclared (first use in this function)
ssl_proxy.c:197: warning: format &#8216;%.256s&#8217; expects type &#8216;char *&#8217;, but argument 3 has type &#8216;int&#8217;
ssl_proxy.c:198: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
ssl_proxy.c:200: warning: implicit declaration of function &#8216;SSL_CTX_set_tmp_rsa_callback&#8217;
ssl_proxy.c:200: error: &#8216;tmp_rsa_cb&#8217; undeclared (first use in this function)
ssl_proxy.c:214: warning: implicit declaration of function &#8216;SSL_CTX_load_verify_locations&#8217;
ssl_proxy.c:215: warning: implicit declaration of function &#8216;SSL_CTX_set_verify&#8217;
ssl_proxy.c:215: error: &#8216;SSL_VERIFY_PEER&#8217; undeclared (first use in this function)
ssl_proxy.c:215: error: &#8216;SSL_VERIFY_FAIL_IF_NO_PEER_CERT&#8217; undeclared (first use in this function)
ssl_proxy.c:215: error: &#8216;SSL_VERIFY_CLIENT_ONCE&#8217; undeclared (first use in this function)
ssl_proxy.c: In function &#8216;client_init&#8217;:
ssl_proxy.c:229: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
ssl_proxy.c:241: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
ssl_proxy.c:245: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
ssl_proxy.c: In function &#8216;conn_accept&#8217;:
ssl_proxy.c:271: error: &#8216;Conn&#8217; has no member named &#8216;ssl_conn&#8217;
ssl_proxy.c:271: warning: implicit declaration of function &#8216;SSL_new&#8217;
ssl_proxy.c:271: error: &#8216;server_ssl_ctx&#8217; undeclared (first use in this function)
ssl_proxy.c:272: warning: implicit declaration of function &#8216;SSL_set_fd&#8217;
ssl_proxy.c:272: error: &#8216;Conn&#8217; has no member named &#8216;ssl_conn&#8217;
ssl_proxy.c:286: warning: implicit declaration of function &#8216;BIO_set_nbio&#8217;
ssl_proxy.c:286: warning: implicit declaration of function &#8216;SSL_get_rbio&#8217;
ssl_proxy.c:286: error: &#8216;Conn&#8217; has no member named &#8216;ssl_conn&#8217;
ssl_proxy.c:287: warning: implicit declaration of function &#8216;SSL_get_wbio&#8217;
ssl_proxy.c:287: error: &#8216;Conn&#8217; has no member named &#8216;ssl_conn&#8217;
ssl_proxy.c:290: error: &#8216;Conn&#8217; has no member named &#8216;scbuf_b&#8217;
ssl_proxy.c:290: error: &#8216;Conn&#8217; has no member named &#8216;scbuf&#8217;
ssl_proxy.c:290: error: &#8216;Conn&#8217; has no member named &#8216;scbuf_e&#8217;
ssl_proxy.c:290: error: &#8216;Conn&#8217; has no member named &#8216;scbuf&#8217;
ssl_proxy.c:291: error: &#8216;Conn&#8217; has no member named &#8216;csbuf_b&#8217;
ssl_proxy.c:291: error: &#8216;Conn&#8217; has no member named &#8216;csbuf&#8217;
ssl_proxy.c:291: error: &#8216;Conn&#8217; has no member named &#8216;csbuf_e&#8217;
ssl_proxy.c:291: error: &#8216;Conn&#8217; has no member named &#8216;csbuf&#8217;
ssl_proxy.c: In function &#8216;conn_ssl_accept&#8217;:
ssl_proxy.c:296: warning: implicit declaration of function &#8216;SSL_accept&#8217;
ssl_proxy.c:296: error: &#8216;Conn&#8217; has no member named &#8216;ssl_conn&#8217;
ssl_proxy.c:299: warning: implicit declaration of function &#8216;SSL_get_error&#8217;
ssl_proxy.c:299: error: &#8216;Conn&#8217; has no member named &#8216;ssl_conn&#8217;
ssl_proxy.c:301: error: &#8216;SSL_ERROR_WANT_READ&#8217; undeclared (first use in this function)
ssl_proxy.c:301: error: &#8216;SSL_ERROR_WANT_WRITE&#8217; undeclared (first use in this function)
ssl_proxy.c:305: warning: implicit declaration of function &#8216;ERR_print_errors_fp&#8217;
ssl_proxy.c:312: warning: implicit declaration of function &#8216;SSL_free&#8217;
ssl_proxy.c:312: error: &#8216;Conn&#8217; has no member named &#8216;ssl_conn&#8217;
ssl_proxy.c:314: error: &#8216;Conn&#8217; has no member named &#8216;client_sock&#8217;
ssl_proxy.c:336: error: &#8216;Conn&#8217; has no member named &#8216;client_sock&#8217;
ssl_proxy.c:337: error: &#8216;Conn&#8217; has no member named &#8216;client_sock&#8217;
ssl_proxy.c:338: error: &#8216;errno&#8217; undeclared (first use in this function)
ssl_proxy.c:339: error: &#8216;Conn&#8217; has no member named &#8216;ssl_conn&#8217;
ssl_proxy.c:341: error: &#8216;Conn&#8217; has no member named &#8216;client_sock&#8217;
ssl_proxy.c:345: error: &#8216;Conn&#8217; has no member named &#8216;client_sock&#8217;
ssl_proxy.c: In function &#8216;conn_close_client&#8217;:
ssl_proxy.c:382: error: &#8216;Conn&#8217; has no member named &#8216;client_sock&#8217;
ssl_proxy.c:383: error: &#8216;Conn&#8217; has no member named &#8216;client_sock&#8217;
ssl_proxy.c:384: error: &#8216;Conn&#8217; has no member named &#8216;client_sock&#8217;
ssl_proxy.c:385: error: &#8216;Conn&#8217; has no member named &#8216;client_sock&#8217;
ssl_proxy.c: In function &#8216;conn_close_server&#8217;:
ssl_proxy.c:391: error: &#8216;Conn&#8217; has no member named &#8216;ssl_conn&#8217;
ssl_proxy.c:395: error: &#8216;Conn&#8217; has no member named &#8216;client_sock&#8217;
ssl_proxy.c: In function &#8216;sighandler&#8217;:
ssl_proxy.c:407: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
ssl_proxy.c: In function &#8216;main&#8217;:
ssl_proxy.c:429: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
ssl_proxy.c:440: warning: implicit declaration of function &#8216;atoi&#8217;
ssl_proxy.c:513: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
ssl_proxy.c:518: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
ssl_proxy.c:522: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
ssl_proxy.c:531: warning: implicit declaration of function &#8216;malloc&#8217;
ssl_proxy.c:531: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
ssl_proxy.c:535: error: &#8216;Conn&#8217; has no member named &#8216;scbuf&#8217;
ssl_proxy.c:536: error: &#8216;Conn&#8217; has no member named &#8216;scbuf_b&#8217;
ssl_proxy.c:536: error: &#8216;Conn&#8217; has no member named &#8216;scbuf&#8217;
ssl_proxy.c:536: error: &#8216;Conn&#8217; has no member named &#8216;scbuf_e&#8217;
ssl_proxy.c:536: error: &#8216;Conn&#8217; has no member named &#8216;scbuf&#8217;
ssl_proxy.c:537: error: &#8216;Conn&#8217; has no member named &#8216;csbuf&#8217;
ssl_proxy.c:538: error: &#8216;Conn&#8217; has no member named &#8216;csbuf_b&#8217;
ssl_proxy.c:538: error: &#8216;Conn&#8217; has no member named &#8216;csbuf&#8217;
ssl_proxy.c:538: error: &#8216;Conn&#8217; has no member named &#8216;csbuf_e&#8217;
ssl_proxy.c:538: error: &#8216;Conn&#8217; has no member named &#8216;csbuf&#8217;
ssl_proxy.c:566: error: &#8216;Conn&#8217; has no member named &#8216;client_sock&#8217;
ssl_proxy.c:567: error: &#8216;errno&#8217; undeclared (first use in this function)
ssl_proxy.c:567: error: &#8216;EINPROGRESS&#8217; undeclared (first use in this function)
ssl_proxy.c:571: error: &#8216;Conn&#8217; has no member named &#8216;client_sock&#8217;
ssl_proxy.c:572: error: &#8216;Conn&#8217; has no member named &#8216;ssl_conn&#8217;
ssl_proxy.c:581: error: &#8216;X509&#8217; undeclared (first use in this function)
ssl_proxy.c:581: error: &#8216;cert&#8217; undeclared (first use in this function)
ssl_proxy.c:582: error: &#8216;X509_NAME&#8217; undeclared (first use in this function)
ssl_proxy.c:582: error: &#8216;xn&#8217; undeclared (first use in this function)
ssl_proxy.c:587: warning: implicit declaration of function &#8216;SSL_get_peer_certificate&#8217;
ssl_proxy.c:587: error: &#8216;Conn&#8217; has no member named &#8216;ssl_conn&#8217;
ssl_proxy.c:589: warning: implicit declaration of function &#8216;X509_get_subject_name&#8217;
ssl_proxy.c:590: warning: implicit declaration of function &#8216;X509_NAME_get_text_by_NID&#8217;
ssl_proxy.c:590: error: &#8216;NID_commonName&#8217; undeclared (first use in this function)
ssl_proxy.c:592: error: &#8216;Conn&#8217; has no member named &#8216;csbuf_e&#8217;
ssl_proxy.c:592: error: &#8216;Conn&#8217; has no member named &#8216;csbuf_b&#8217;
ssl_proxy.c:596: error: &#8216;Conn&#8217; has no member named &#8216;csbuf&#8217;
ssl_proxy.c:602: error: &#8216;Conn&#8217; has no member named &#8216;csbuf_e&#8217;
ssl_proxy.c:602: error: &#8216;Conn&#8217; has no member named &#8216;csbuf&#8217;
ssl_proxy.c:603: warning: implicit declaration of function &#8216;SSL_read&#8217;
ssl_proxy.c:603: error: &#8216;Conn&#8217; has no member named &#8216;ssl_conn&#8217;
ssl_proxy.c:603: error: &#8216;Conn&#8217; has no member named &#8216;csbuf_e&#8217;
ssl_proxy.c:609: error: &#8216;EAGAIN&#8217; undeclared (first use in this function)
ssl_proxy.c:614: error: &#8216;Conn&#8217; has no member named &#8216;csbuf_e&#8217;
ssl_proxy.c:618: error: &#8216;Conn&#8217; has no member named &#8216;csbuf_e&#8217;
ssl_proxy.c:618: error: &#8216;Conn&#8217; has no member named &#8216;csbuf_b&#8217;
ssl_proxy.c:619: error: &#8216;Conn&#8217; has no member named &#8216;client_sock&#8217;
ssl_proxy.c:619: error: &#8216;Conn&#8217; has no member named &#8216;csbuf_b&#8217;
ssl_proxy.c:620: error: &#8216;Conn&#8217; has no member named &#8216;csbuf_b&#8217;
ssl_proxy.c:622: error: &#8216;Conn&#8217; has no member named &#8216;csbuf_b&#8217;
ssl_proxy.c:626: error: &#8216;Conn&#8217; has no member named &#8216;csbuf_b&#8217;
ssl_proxy.c:626: error: &#8216;Conn&#8217; has no member named &#8216;csbuf_e&#8217;
ssl_proxy.c:626: error: &#8216;Conn&#8217; has no member named &#8216;csbuf&#8217;
ssl_proxy.c:630: error: &#8216;Conn&#8217; has no member named &#8216;csbuf_b&#8217;
ssl_proxy.c:630: error: &#8216;Conn&#8217; has no member named &#8216;csbuf_e&#8217;
ssl_proxy.c:631: error: &#8216;Conn&#8217; has no member named &#8216;csbuf_b&#8217;
ssl_proxy.c:631: error: &#8216;Conn&#8217; has no member named &#8216;csbuf_e&#8217;
ssl_proxy.c:631: error: &#8216;Conn&#8217; has no member named &#8216;csbuf&#8217;
ssl_proxy.c:635: error: &#8216;Conn&#8217; has no member named &#8216;csbuf_e&#8217;
ssl_proxy.c:635: error: &#8216;Conn&#8217; has no member named &#8216;csbuf_b&#8217;
ssl_proxy.c:640: error: &#8216;Conn&#8217; has no member named &#8216;scbuf_e&#8217;
ssl_proxy.c:640: error: &#8216;Conn&#8217; has no member named &#8216;scbuf&#8217;
ssl_proxy.c:640: error: &#8216;Conn&#8217; has no member named &#8216;client_sock&#8217;
ssl_proxy.c:641: error: &#8216;Conn&#8217; has no member named &#8216;client_sock&#8217;
ssl_proxy.c:641: error: &#8216;Conn&#8217; has no member named &#8216;scbuf_e&#8217;
ssl_proxy.c:651: error: &#8216;Conn&#8217; has no member named &#8216;scbuf_e&#8217;
ssl_proxy.c:654: error: &#8216;Conn&#8217; has no member named &#8216;scbuf_e&#8217;
ssl_proxy.c:654: error: &#8216;Conn&#8217; has no member named &#8216;scbuf_b&#8217;
ssl_proxy.c:655: warning: implicit declaration of function &#8216;SSL_write&#8217;
ssl_proxy.c:655: error: &#8216;Conn&#8217; has no member named &#8216;ssl_conn&#8217;
ssl_proxy.c:655: error: &#8216;Conn&#8217; has no member named &#8216;scbuf_b&#8217;
ssl_proxy.c:656: error: &#8216;Conn&#8217; has no member named &#8216;scbuf&#8217;
ssl_proxy.c:657: error: &#8216;Conn&#8217; has no member named &#8216;scbuf_b&#8217;
ssl_proxy.c:659: error: &#8216;Conn&#8217; has no member named &#8216;scbuf_b&#8217;
ssl_proxy.c:662: error: &#8216;Conn&#8217; has no member named &#8216;scbuf_b&#8217;
ssl_proxy.c:662: error: &#8216;Conn&#8217; has no member named &#8216;scbuf_e&#8217;
ssl_proxy.c:662: error: &#8216;Conn&#8217; has no member named &#8216;scbuf&#8217;
ssl_proxy.c:665: error: &#8216;Conn&#8217; has no member named &#8216;scbuf_b&#8217;
ssl_proxy.c:665: error: &#8216;Conn&#8217; has no member named &#8216;scbuf_e&#8217;
ssl_proxy.c:666: error: &#8216;Conn&#8217; has no member named &#8216;scbuf_b&#8217;
ssl_proxy.c:666: error: &#8216;Conn&#8217; has no member named &#8216;scbuf_e&#8217;
ssl_proxy.c:666: error: &#8216;Conn&#8217; has no member named &#8216;scbuf&#8217;
ssl_proxy.c:670: error: &#8216;Conn&#8217; has no member named &#8216;scbuf_e&#8217;
ssl_proxy.c:670: error: &#8216;Conn&#8217; has no member named &#8216;scbuf_b&#8217;
make: *** [ssl_proxy.o] Error 1
```

And here is what I get when I try to compile the linsql.c file
```
root@root:/# gcc -o linsql linsql.c
linsql.c:1: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;BugTraq&#8217;
linsql.c:4:1: warning: multi-character character constant
linsql.c:7:55: warning: missing terminating ' character
linsql.c:7: error: missing terminating ' character
linsql.c:8:1: warning: character constant too long for its type
linsql.c:9:37: warning: multi-character character constant
linsql.c:10: error: stray &#8216;`&#8217; in program
linsql.c:10: error: stray &#8216;\&#8217; in program
linsql.c:10:85: warning: missing terminating ' character
linsql.c:10: error: missing terminating ' character
linsql.c:12:20: warning: character constant too long for its type
linsql.c:12:57: warning: missing terminating ' character
linsql.c:12: error: missing terminating ' character
linsql.c:20: error: stray &#8216;@&#8217; in program
linsql.c:97:36: error: ../freetds/include/tds.h: No such file or directory
In file included from /usr/include/stdio.h:75,
                 from linsql.c:98:
/usr/include/libio.h:332: error: expected specifier-qualifier-list before &#8216;size_t&#8217;
/usr/include/libio.h:364: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/libio.h:373: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/libio.h:495: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;_IO_sgetn&#8217;
In file included from linsql.c:98:
/usr/include/stdio.h:296: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/stdio.h:302: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/stdio.h:314: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/stdio.h:321: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/stdio.h:363: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/stdio.h:365: error: format string argument not a string type
/usr/include/stdio.h:367: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/stdio.h:639: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/stdio.h:642: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/stdio.h:652: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/stdio.h:682: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;fread&#8217;
/usr/include/stdio.h:688: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;fwrite&#8217;
/usr/include/stdio.h:710: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;fread_unlocked&#8217;
/usr/include/stdio.h:712: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;fwrite_unlocked&#8217;
In file included from linsql.c:99:
/usr/include/unistd.h:357: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/unistd.h:363: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/unistd.h:507: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
In file included from linsql.c:99:
/usr/include/unistd.h:618: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;confstr&#8217;
/usr/include/unistd.h:790: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/unistd.h:826: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/unistd.h:837: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/unistd.h:873: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
In file included from linsql.c:99:
/usr/include/unistd.h:895: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/unistd.h:902: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/unistd.h:913: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/unistd.h:915: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/unistd.h:933: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/unistd.h:934: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
In file included from /usr/include/sys/uio.h:29,
                 from /usr/include/sys/socket.h:28,
                 from linsql.c:104:
/usr/include/bits/uio.h:47: error: expected specifier-qualifier-list before &#8216;size_t&#8217;
In file included from /usr/include/sys/socket.h:40,
                 from linsql.c:104:
/usr/include/bits/socket.h:251: error: expected specifier-qualifier-list before &#8216;size_t&#8217;
/usr/include/bits/socket.h:265: error: expected specifier-qualifier-list before &#8216;size_t&#8217;
In file included from linsql.c:104:
/usr/include/sys/socket.h:141: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/sys/socket.h:148: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/sys/socket.h:155: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/sys/socket.h:166: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
In file included from /usr/include/signal.h:356,
                 from linsql.c:105:
/usr/include/bits/sigstack.h:54: error: expected specifier-qualifier-list before &#8216;size_t&#8217;
linsql.c:109: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;interactive&#8217;
linsql.c:111:21: error: invalid suffix "Megs." on integer constant
linsql.c:141: warning: data definition has no type or storage class
linsql.c:158: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
linsql.c:176: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;void&#8217;
linsql.c:177: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;for&#8217;
linsql.c:185: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
linsql.c:186: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
linsql.c: In function &#8216;main&#8217;:
linsql.c:202: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
linsql.c:224:10: warning: missing terminating " character
linsql.c:224: error: missing terminating " character
linsql.c:225: error: stray &#8216;\&#8217; in program
linsql.c:225: error: &#8216;mode&#8217; undeclared (first use in this function)
linsql.c:225: error: (Each undeclared identifier is reported only once
linsql.c:225: error: for each function it appears in.)
linsql.c:225: error: expected &#8216;)&#8217; before &#8216;n&#8217;
linsql.c:225:7: warning: missing terminating " character
linsql.c:225: error: missing terminating " character
linsql.c:227:10: warning: missing terminating " character
linsql.c:227: error: missing terminating " character
linsql.c:228: error: stray &#8216;\&#8217; in program
linsql.c:228:24: warning: missing terminating " character
linsql.c:228: error: missing terminating " character
linsql.c:229:10: warning: missing terminating " character
linsql.c:229: error: missing terminating " character
linsql.c:230: error: stray &#8216;\&#8217; in program
linsql.c:230:24: warning: missing terminating " character
linsql.c:230: error: missing terminating " character
linsql.c:231:10: warning: missing terminating " character
linsql.c:231: error: missing terminating " character
linsql.c:232: error: stray &#8216;\&#8217; in program
linsql.c:232:25: warning: missing terminating " character
linsql.c:232: error: missing terminating " character
linsql.c:233:10: warning: missing terminating " character
linsql.c:233: error: missing terminating " character
linsql.c:234: error: stray &#8216;\&#8217; in program
linsql.c:234: error: stray &#8216;\&#8217; in program
linsql.c:234:26: warning: missing terminating " character
linsql.c:234: error: missing terminating " character
linsql.c:236:10: warning: missing terminating " character
linsql.c:236: error: missing terminating " character
linsql.c:237:15: warning: multi-character character constant
linsql.c:237: error: stray &#8216;\&#8217; in program
linsql.c:237:21: warning: missing terminating " character
linsql.c:237: error: missing terminating " character
linsql.c:238:10: warning: missing terminating " character
linsql.c:238: error: missing terminating " character
linsql.c:239: error: stray &#8216;\&#8217; in program
linsql.c:239:24: warning: missing terminating " character
linsql.c:239: error: missing terminating " character
linsql.c:240:10: warning: missing terminating " character
linsql.c:240: error: missing terminating " character
linsql.c:241: error: stray &#8216;\&#8217; in program
linsql.c:241: error: stray &#8216;\&#8217; in program
linsql.c:241:20: warning: missing terminating " character
linsql.c:241: error: missing terminating " character
linsql.c:242:10: warning: missing terminating " character
linsql.c:242: error: missing terminating " character
linsql.c:243: error: stray &#8216;\&#8217; in program
linsql.c:243: error: stray &#8216;\&#8217; in program
linsql.c:243:36: warning: missing terminating " character
linsql.c:243: error: missing terminating " character
linsql.c:244:10: warning: missing terminating " character
linsql.c:244: error: missing terminating " character
linsql.c:245:3: error: too many decimal points in number
linsql.c:245: error: stray &#8216;\&#8217; in program
linsql.c:245:17: warning: missing terminating " character
linsql.c:245: error: missing terminating " character
linsql.c:246:10: warning: missing terminating " character
linsql.c:246: error: missing terminating " character
linsql.c:247: error: stray &#8216;\&#8217; in program
linsql.c:247: error: stray &#8216;\&#8217; in program
linsql.c:247:32: warning: missing terminating " character
linsql.c:247: error: missing terminating " character
linsql.c:425:70: warning: missing terminating " character
linsql.c:425: error: missing terminating " character
linsql.c:426:9: warning: missing terminating " character
linsql.c:426: error: missing terminating " character
linsql.c:429:76: warning: missing terminating " character
linsql.c:429: error: missing terminating " character
linsql.c:430:9: warning: missing terminating " character
linsql.c:430: error: missing terminating " character
linsql.c:530:11: warning: missing terminating " character
linsql.c:530: error: missing terminating " character
linsql.c:531: error: stray &#8216;\&#8217; in program
linsql.c:531:14: warning: missing terminating " character
linsql.c:531: error: missing terminating " character
linsql.c:541:11: warning: missing terminating " character
linsql.c:541: error: missing terminating " character
linsql.c:542: error: stray &#8216;\&#8217; in program
linsql.c:542:22: warning: missing terminating " character
linsql.c:542: error: missing terminating " character
linsql.c:545:11: warning: missing terminating " character
linsql.c:545: error: missing terminating " character
linsql.c:546: error: stray &#8216;\&#8217; in program
linsql.c:546:13: warning: missing terminating " character
linsql.c:546: error: missing terminating " character
linsql.c:549:11: warning: missing terminating " character
linsql.c:549: error: missing terminating " character
linsql.c:550: error: stray &#8216;\&#8217; in program
linsql.c:550:26: warning: missing terminating " character
linsql.c:550: error: missing terminating " character
linsql.c:551:11: warning: missing terminating " character
linsql.c:551: error: missing terminating " character
linsql.c:552: error: stray &#8216;\&#8217; in program
linsql.c:552:11: warning: missing terminating " character
linsql.c:552: error: missing terminating " character
linsql.c:553:11: warning: missing terminating " character
linsql.c:553: error: missing terminating " character
linsql.c:554: error: stray &#8216;\&#8217; in program
linsql.c:655:14: warning: missing terminating " character
linsql.c:655: error: missing terminating " character
linsql.c:656: error: stray &#8216;\&#8217; in program
linsql.c:656:15: warning: missing terminating " character
linsql.c:656: error: missing terminating " character
linsql.c:661:15: warning: missing terminating " character
linsql.c:661: error: missing terminating " character
linsql.c:662:13: warning: missing terminating " character
linsql.c:662: error: missing terminating " character
linsql.c:670:15: warning: missing terminating " character
linsql.c:670: error: missing terminating " character
linsql.c:671:13: warning: missing terminating " character
linsql.c:671: error: missing terminating " character
linsql.c:1032:24: warning: missing terminating " character
linsql.c:1032: error: missing terminating " character
linsql.c:1033: error: stray &#8216;\&#8217; in program
linsql.c:1033: error: stray &#8216;\&#8217; in program
linsql.c:1033:29: warning: missing terminating ' character
linsql.c:1033: error: missing terminating ' character
linsql.c:1046:11: warning: missing terminating " character
linsql.c:1046: error: missing terminating " character
linsql.c:1047: error: stray &#8216;\&#8217; in program
linsql.c:1047:6: warning: missing terminating " character
linsql.c:1047: error: missing terminating " character
linsql.c:1343:14: warning: missing terminating " character
linsql.c:1343: error: missing terminating " character
linsql.c:1344: error: stray &#8216;\&#8217; in program
linsql.c:1344:23: warning: missing terminating ' character
linsql.c:1344: error: missing terminating ' character
linsql.c:1494: error: expected declaration or statement at end of input
linsql.c:1494: error: expected declaration or statement at end of input
```

Any help, tips or pointers would be awesome!
Thanks

---

### Post by oldos2er on 2012-06-18
Moved to Other OS/Distro Talk.

---

