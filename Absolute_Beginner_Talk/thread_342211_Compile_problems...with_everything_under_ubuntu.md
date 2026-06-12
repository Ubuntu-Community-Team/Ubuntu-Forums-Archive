---
title: "Compile problems...with everything under ubuntu"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by KarlGibbs36 on 2007-01-19
ok, this is one of the reasons i still use windows, installing programs. Firstly i will say that i like and can get along with the apt-get tools very well, it works great, but when it comes to anything that isnt in a .deb or in the ubuntu repositorys, orr wlan-ng for that matter, nothing works. 

it seems like every bit of .c source code i download from anywhere has bugs and errors in the code, why do people release it onto the internet full of problems??....and another thing, all these .h include files and other stuff, why cant they just be packaged with the source code files? 

i mean, surely the developers of the software had access to them, and im sure its not gonna hurt to stick em in the .zip file is it, unless there are laws about distributing particular pieces of code.

for example, today i tryed to compile a custom version of wlan-ng, hostap, void11, and bluesnarfer. i installed the kernel headers using apt and tryed to compile bluesnarfer, guess what? it couldnt find the include files, so i copyed them over to the apropriate folders where i had the bluesnarfer source, and it found them but said they were full of errors too!!!! 

what the hell is going on here?? the only thing i have ever had compile smoothly is aircrack on an old version of ubuntu and that is the ONLY thing i have ever managed to compile under linux..... i love ubuntu, it looks like, it has nice features, its secure and has a more user friendly face to it, but i might have to get rid of it because i simply cant compile any programs under it and that just p***es me off. At least i can install pretty much anything under windows.  

Another thing, when you cant find certain header files, or the ones you have dont work, where the hell do you go to find em online? is there any websites which let you just select and download header files? because in my experience i have come across several websites with the 'same' header file, but the code is slightly different from site to site, and at the end of trying every single one, guess what? it does not work,

Can anyone help me out here or explain to me why everything seems to fail misribly when compiling under ubuntu (or any linux Distro for that matter, i have tryed a few) and tell me what i have to do to make at least something work? and if there is any good websites for downloading header files that work.

Example of output after moving bluetooth header files to bluesnarfer directory

nexus@Oblivion:~/bluesnarfer$ make --ignore-errors
gcc -Iinclude -W -g3 -lbluetooth src/bluesnarfer.c -o bluesnarfer
In file included from src/bluesnarfer.c:29:
include/bluetooth/bluetooth.h:35:22: error: net/sock.h: No such file or directory
In file included from src/bluesnarfer.c:29:
include/bluetooth/bluetooth.h: In function ‘bacpy’:
include/bluetooth/bluetooth.h:127: warning: incompatible implicit declaration of built-in function ‘memcpy’
include/bluetooth/bluetooth.h: At top level:
[B]include/bluetooth/bluetooth.h:144: error: field ‘accept_q’ has incomplete type
include/bluetooth/bluetooth.h:150: error: expected specifier-qualifier-list before ‘rwlock_t’[/B]
include/bluetooth/bluetooth.h:153: warning: ‘struct net_proto_family’ declared inside parameter list
include/bluetooth/bluetooth.h:153: warning: its scope is only this definition or declaration, which is probably not what you want
include/bluetooth/bluetooth.h:155: warning: ‘struct socket’ declared inside parameter list
include/bluetooth/bluetooth.h:158: warning: ‘struct scm_cookie’ declared inside parameter list
include/bluetooth/bluetooth.h:158: warning: ‘struct socket’ declared inside parameter list
**include/bluetooth/bluetooth.h:159: error: expected declaration specifiers or ‘...’ before ‘poll_table’**
include/bluetooth/bluetooth.h:159: warning: ‘struct socket’ declared inside parameter list
include/bluetooth/bluetooth.h:159: warning: ‘struct file’ declared inside parameter list
include/bluetooth/bluetooth.h:163: warning: ‘struct socket’ declared inside parameter list
include/bluetooth/bluetooth.h: In function ‘bluez_skb_alloc’:
include/bluetooth/bluetooth.h:175: warning: assignment makes pointer from integer without a cast
**include/bluetooth/bluetooth.h:177: error: dereferencing pointer to incomplete type**
include/bluetooth/bluetooth.h: In function ‘bluez_skb_send_alloc’:
include/bluetooth/bluetooth.h:187: warning: assignment makes pointer from integer without a cast
**include/bluetooth/bluetooth.h:189: error: dereferencing pointer to incomplete type**
include/bluetooth/bluetooth.h: In function ‘skb_frags_no’:
[B]include/bluetooth/bluetooth.h:197: error: invalid type argument of ‘->’
include/bluetooth/bluetooth.h:200: error: dereferencing pointer to incomplete type[/B]
include/bluetooth/bluetooth.h:200: warning: left-hand operand of comma expression has no effect
include/bluetooth/bluetooth.h:200: warning: value computed is not used
**src/bluesnarfer.c:31:31: error: bluetooth/hci_lib.h: No such file or directory**
In file included from src/bluesnarfer.c:32:
include/bluetooth/rfcomm.h: At top level:
[B]include/bluetooth/rfcomm.h:112: error: expected specifier-qualifier-list before ‘u8’
include/bluetooth/rfcomm.h:118: error: expected specifier-qualifier-list before ‘u8’
include/bluetooth/rfcomm.h:125: error: expected specifier-qualifier-list before ‘u8’
include/bluetooth/rfcomm.h:130: error: expected specifier-qualifier-list before ‘u8’
include/bluetooth/rfcomm.h:140: error: expected specifier-qualifier-list before ‘u8’
include/bluetooth/rfcomm.h:150: error: expected specifier-qualifier-list before ‘u8’
include/bluetooth/rfcomm.h:155: error: expected specifier-qualifier-list before ‘u8’
include/bluetooth/rfcomm.h:162: error: field ‘list’ has incomplete type
include/bluetooth/rfcomm.h:166: error: expected specifier-qualifier-list before ‘atomic_t’
include/bluetooth/rfcomm.h:177: error: field ‘list’ has incomplete type
include/bluetooth/rfcomm.h:179: error: field ‘tx_queue’ has incomplete type
include/bluetooth/rfcomm.h:180: error: field ‘timer’ has incomplete type
include/bluetooth/rfcomm.h:182: error: expected specifier-qualifier-list before ‘spinlock_t’
include/bluetooth/rfcomm.h:245: error: expected declaration specifiers or ‘...’ before ‘u8’
include/bluetooth/rfcomm.h:248: error: expected declaration specifiers or ‘...’ before ‘u8’
include/bluetooth/rfcomm.h:249: error: expected declaration specifiers or ‘...’ before ‘u8’[/B]
include/bluetooth/rfcomm.h: In function ‘rfcomm_dlc_hold’:
**include/bluetooth/rfcomm.h:256: error: ‘struct rfcomm_dlc’ has no member named ‘refcnt’**
include/bluetooth/rfcomm.h: In function ‘rfcomm_dlc_put’:
**include/bluetooth/rfcomm.h:261: error: ‘struct rfcomm_dlc’ has no member named ‘refcnt’**
include/bluetooth/rfcomm.h: At top level:
[B]include/bluetooth/rfcomm.h:265: error: expected ‘)’ before ‘(’ token
include/bluetooth/rfcomm.h:266: error: expected ‘)’ before ‘(’ token[/B]
include/bluetooth/rfcomm.h: In function ‘rfcomm_dlc_throttle’:
**include/bluetooth/rfcomm.h:270: error: ‘struct rfcomm_dlc’ has no member named ‘flags’**
include/bluetooth/rfcomm.h: In function ‘rfcomm_dlc_unthrottle’:
**include/bluetooth/rfcomm.h:276: error: ‘struct rfcomm_dlc’ has no member named ‘flags’**
include/bluetooth/rfcomm.h: In function ‘rfcomm_session_hold’:
**include/bluetooth/rfcomm.h:290: error: ‘struct rfcomm_session’ has no member named ‘refcnt’**
include/bluetooth/rfcomm.h: In function ‘rfcomm_session_put’:
**include/bluetooth/rfcomm.h:295: error: ‘struct rfcomm_session’ has no member named ‘refcnt’**
include/bluetooth/rfcomm.h: At top level:
**include/bluetooth/rfcomm.h:300: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rfcomm_crc_table’**
**include/bluetooth/rfcomm.h:306: error: expected specifier-qualifier-list before ‘u8’**
**include/bluetooth/rfcomm.h:313: error: expected specifier-qualifier-list before ‘u8’**
**include/bluetooth/rfcomm.h:319: error: expected declaration specifiers or ‘...’ before ‘u8’**
**include/bluetooth/rfcomm.h:336: error: expected specifier-qualifier-list before ‘s16’**
**include/bluetooth/rfcomm.h:344: error: expected specifier-qualifier-list before ‘s16’**
**include/bluetooth/rfcomm.h:353: error: expected specifier-qualifier-list before ‘u16’**
src/bluesnarfer.c: In function ‘parse_rw’:
src/bluesnarfer.c:39: warning: incompatible implicit declaration of built-in function ‘strchr’
src/bluesnarfer.c: In function ‘bt_get_remote_name’:
src/bluesnarfer.c:203: warning: incompatible implicit declaration of built-in function ‘memcpy’
**src/bluesnarfer.c:223: error: ‘HCI_OE_USER_ENDED_CONNECTION’ undeclared (first use in this function)**
**src/bluesnarfer.c:223: error: (Each undeclared identifier is reported only once**
**src/bluesnarfer.c:223: error: for each function it appears in.)**
src/bluesnarfer.c: In function ‘rfcomm_read’:
src/bluesnarfer.c:251: warning: incompatible implicit declaration of built-in function ‘strlen’
src/bluesnarfer.c: In function ‘bt_rfcomm’:
src/bluesnarfer.c:278: warning: incompatible implicit declaration of built-in function ‘memset’
**src/bluesnarfer.c:281: error: ‘struct rfcomm_dev_req’ has no member named ‘dev_id’**
**src/bluesnarfer.c:282: error: ‘struct rfcomm_dev_req’ has no member named ‘channel’**
src/bluesnarfer.c:284: warning: incompatible implicit declaration of built-in function ‘memcpy’
**src/bluesnarfer.c:284: error: ‘struct rfcomm_dev_req’ has no member named ‘src’**
**src/bluesnarfer.c:285: error: ‘struct rfcomm_dev_req’ has no member named ‘dst’**
src/bluesnarfer.c: In function ‘custom_cmd’:
src/bluesnarfer.c:382: warning: incompatible implicit declaration of built-in function ‘strstr’
src/bluesnarfer.c:390: warning: incompatible implicit declaration of built-in function ‘strlen’
src/bluesnarfer.c: In function ‘bt_rfcomm_rel’:
src/bluesnarfer.c:413: warning: incompatible implicit declaration of built-in function ‘memset’
**src/bluesnarfer.c:414: error: ‘struct rfcomm_dev_req’ has no member named ‘dev_id’**
src/bluesnarfer.c: In function ‘rw_cmd’:
src/bluesnarfer.c:434: warning: incompatible implicit declaration of built-in function ‘strlen’
src/bluesnarfer.c:442: warning: incompatible implicit declaration of built-in function ‘strlen’
src/bluesnarfer.c:455: warning: incompatible implicit declaration of built-in function ‘strlen’
src/bluesnarfer.c: In function ‘parse’:
src/bluesnarfer.c:500: warning: incompatible implicit declaration of built-in function ‘memset’
src/bluesnarfer.c:503: warning: incompatible implicit declaration of built-in function ‘strchr’
src/bluesnarfer.c:506: warning: incompatible implicit declaration of built-in function ‘strlen’
src/bluesnarfer.c: In function ‘search_cmd’:
src/bluesnarfer.c:550: warning: incompatible implicit declaration of built-in function ‘strlen’
src/bluesnarfer.c: In function ‘list_cmd’:
src/bluesnarfer.c:600: warning: incompatible implicit declaration of built-in function ‘strlen’
src/bluesnarfer.c:614: warning: incompatible implicit declaration of built-in function ‘strchr’
src/bluesnarfer.c:622: warning: incompatible implicit declaration of built-in function ‘strstr’
src/bluesnarfer.c: In function ‘info_cmd’:
src/bluesnarfer.c:643: warning: incompatible implicit declaration of built-in function ‘strlen’
make: [bluesnarfer] Error 1 (ignored)

---

### Post by tagra123 on 2007-01-19
Try installing these:

```
sudo aptitude install linux-headers-`uname -r` build-essential
```


The above installs should eliminate most of your problems. 

The other thing you will usually run in to is missing dependencies. When a dependency is needed -- in the 2nd terminal apt-get or aptitude the missing file or package and try again.

You can use apt-get in place of aptitude. Aptitude seems better to me.

Before compiling anything make sure there isn't a deb for it already. I rarely compile anything and can do on my machine anything I could do in windows with the help of wine and vmware.  Make sure you check the universe and multiverse repositories to get some of the features that make ubuntu useful.

---

### Post by KarlGibbs36 on 2007-01-20
i have run "sudo aptitude install linux-headers-`uname -r` build-essential" and both packages have allready been installed. i will go and look at the ubuntu repositorys now but what kind of stuff am i looking for? how do i identify which package to download acording to the error?

cheers

---

### Post by 3rdalbum on 2007-01-20
You usually get error information when you perform the ./configure step - it should tell you the approximate name of what you're missing, e.g.:

Checking for GTK...  Not found.

In that case, you would do a search for libgtk-dev or something similar - "lib" because it's a library, "gtk" because that was what wasn't found, and "-dev" because you need the development libraries to compile the program.

---

### Post by M_o_D on 2007-04-07
I just installed the package "libbluetooth2-dev" and then it worked to compile.

---

