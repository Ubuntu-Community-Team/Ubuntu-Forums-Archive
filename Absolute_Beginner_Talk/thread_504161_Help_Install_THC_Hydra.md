---
title: "Help Install THC Hydra"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by wildseven on 2007-07-18
Hello all. Ok, I downloaded the tarball. Did the whole ./configure make and make install dance and i got some errors. I installed the dependencies ( except SAP R3 which isn't needed ) and Here is the output of my errors.
```
gcc -I. -Wall -O2 -lm -o hydra hydra-vnc.o hydra-pcnfs.o hydra-rexec.o hydra-nntp.o hydra-socks5.o hydra-telnet.o hydra-cisco.o hydra-http.o hydra-ftp.o hydra-imap.o hydra-pop3.o hydra-smb.o hydra-icq.o hydra-cisco-enable.o hydra-ldap.o hydra-mysql.o hydra-http-proxy.o hydra-smbnt.o hydra-mssql.o hydra-snmp.o hydra-cvs.o hydra-smtpauth.o hydra-sapr3.o hydra-ssh2.o hydra-teamspeak.o hydra-postgres.o hydra-rsh.o hydra-rlogin.o hydra-oracle-listener.o hydra-svn.o hydra-pcanywhere.o hydra-sip.o hydra-vmauthd.o hydra-http-proxy-auth-ntlm.o hydra-imap-ntlm.o hydra-pop3-ntlm.o hydra-smtpauth-ntlm.o hydra-http-form.o crc32.o d3des.o md4.o hydra-mod.o ntlm.o hydra.o -lm -lssl -lssh -lcrypto -L/usr/lib -L/usr/local/lib -L/lib -L/usr/lib || echo -e "\nIF YOU RECEIVED THE ERROR MESSAGE \"cannot find -lpq\" DO THE FOLLOWING:\n  make clean; ./configure\n  vi Makefile    <- and remove the \"-lpq\" and \"-DLIBPOSTGRES\" statements\n  make\n"
hydra-ssh2.o: In function `start_ssh2':
hydra-ssh2.c:(.text+0x44): undefined reference to `options_new'
hydra-ssh2.c:(.text+0xac): undefined reference to `options_set_wanted_method'
hydra-ssh2.c:(.text+0xc4): undefined reference to `options_set_wanted_method'
hydra-ssh2.c:(.text+0xd3): undefined reference to `options_set_port'
hydra-ssh2.c:(.text+0xdf): undefined reference to `options_set_host'
hydra-ssh2.c:(.text+0xee): undefined reference to `options_set_username'
hydra-ssh2.c:(.text+0x13f): undefined reference to `ssh_error_code'
collect2: ld returned 1 exit status
-e 
IF YOU RECEIVED THE ERROR MESSAGE "cannot find -lpq" DO THE FOLLOWING:
  make clean; ./configure
  vi Makefile    <- and remove the "-lpq" and "-DLIBPOSTGRES" statements
  make


If men could get pregnant, abortion would be a sacrament

test -e hydra.exe && touch Makefile || strip hydra pw-inspector
strip: 'hydra': No such file
make: [strip] Error 1 (ignored)
test -e hydra.exe && strip hydra.exe pw-inspector.exe || touch hydra
test -e xhydra && strip xhydra || touch Makefile
test -e hydra.exe && touch Makefile || cp hydra pw-inspector /usr/local/bin && cd /usr/local/bin && chmod 755 hydra pw-inspector
test -e hydra.exe && cp hydra.exe pw-inspector.exe /usr/local/bin && cd /usr/local/bin && chmod 755 hydra.exe pw-inspector.exe || touch Makefile
test -e xhydra && cp xhydra /usr/local/bin && cd /usr/local/bin && chmod 755 xhydra
make: [install] Error 1 (ignored)

```

Please help.

---

### Post by wildseven on 2007-07-18
bump?

---

### Post by cus on 2007-08-05
Looks like you might have the wrong version of the libssh installed. 

Version 0.20 that's in the repos isn't backwardly compatible with 0.11. Try downloading, compiling and installing the  version from [http://0xbadc0de.be](http://0xbadc0de.be)

---

