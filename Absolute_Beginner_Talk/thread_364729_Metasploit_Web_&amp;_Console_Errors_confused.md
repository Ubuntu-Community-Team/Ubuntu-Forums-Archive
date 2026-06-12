---
title: "Metasploit Web &amp; Console Errors :confused:"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by Monoxide on 2007-02-18
:confused: I am also having problems with the Metasploit Console & Web Interface. I have installed Open SSL, Ruby, Perl and alot of the other things that are needed to run this application. I have also visited that ethical hacker site and done as they had said for the 2.x firmware and I can get the 2.x working fine just not the 3.0 beta 3

This is the error code I get when trying to launch the web interface or the console
```
./msfweb
./lib/rex/socket/ssl_tcp_server.rb:4:in `require': no such file to load -- openssl (LoadError)
        from ./lib/rex/socket/ssl_tcp_server.rb:4
        from ./lib/rex/socket/comm/local.rb:5:in `require'
        from ./lib/rex/socket/comm/local.rb:5
        from ./lib/rex/socket.rb:22:in `require'
        from ./lib/rex/socket.rb:22
        from ./lib/rex.rb:71:in `require'
        from ./lib/rex.rb:71
        from ./msfweb:9:in `require'
        from ./msfweb:9

```

All the file are in the correct Directory 
```
lib/rex/socket$ ls
comm                   ssl_tcp.rb.ut.rb         tcp.rb
comm.rb                ssl_tcp_server.rb        tcp.rb.ut.rb
parameters.rb          ssl_tcp_server.rb.ut.rb  tcp_server.rb
parameters.rb.ut.rb    subnet_walker.rb         tcp_server.rb.ut.rb
range_walker.rb        subnet_walker.rb.ut.rb   udp.rb
range_walker.rb.ut.rb  switch_board.rb          udp.rb.ut.rb
ssl_tcp.rb             switch_board.rb.ut.rb

```
```
/lib/rex$ ls
arch                 logging             service_manager.rb.ut.rb
arch.rb              logging.rb          service.rb
assembly             nop                 services
codepage.map         parser              socket
compat.rb            payloads            socket.rb
constants.rb         payloads.rb         socket.rb.ut.rb
encoder              peparsey            struct2
encoders             peparsey.rb         struct2.rb
encoding             pescan              sync
evasion.rb           pescan.rb           sync.rb
evasion.rb.ut.rb     poly                test.rb
exceptions.rb        poly.rb             text.rb
exceptions.rb.ut.rb  post                text.rb.ut.rb
exploitation         post.rb             time.rb
file.rb              proto               transformer.rb
file.rb.ut.rb        proto.rb            transformer.rb.ut.rb
io                   proto.rb.ts.rb      ui
job_container.rb     script.rb           ui.rb
LICENSE              service_manager.rb

```

Packages Installed 
Ruby Gen
Ruby Rails
OpenSSL Source
OpenSSL for Ruby
Perl
& lots of other libaries that where posted on the ethical hacker website & others to make this program run properly. I have googled for the past 2 days and have not found a solution to this issue yet. I have read other forum post on the forums and still have no found a solution.

any help or ideas would be great...

---

### Post by Monoxide on 2007-02-18
no ideas?

---

### Post by billyjoebob on 2007-02-27
I'm having the exact same issues when try to run the msfconsole for Metasploit 3.0.  I have postgresql installed and configured.  Oddly enough, the:

gem install postgres

did not work for me but

gem install postgres-pr did, but I have no idea why.  When I try and execute the ruby msfconsole, regardless of the privilege level I get the following error:

./lib/rex/socket/ssl_tcp_server.rb:4:in `require': no such file to load -- openssl (LoadError)
        from ./lib/rex/socket/ssl_tcp_server.rb:4
        from ./lib/rex/socket/comm/local.rb:5
        from ./lib/rex/socket.rb:22
        from ./lib/rex.rb:71
        from ./msfconsole:10

Does anyone have any advice?  I'd love to get 3.0 working.

Thanks,

BJB

---

### Post by billyjoebob on 2007-02-27
Ok, I've solved my own problem, and yours.  It turns out that two crucial commands were missing:

```

# apt-get install libzlib-ruby
# apt-get install libopenssl-ruby

```

Once those modules were installed, the error in question went away.

BJB

---

### Post by fakie_flip on 2007-03-04
> **billyjoebob said:**
> Ok, I've solved my own problem, and yours.  It turns out that two crucial commands were missing:

```

# apt-get install libzlib-ruby
# apt-get install libopenssl-ruby

```

Once those modules were installed, the error in question went away.

BJB

I installed those two, and now i am able to run  msfcli  and msfconsole, but msfweb is not working

```
chris@ubuntu:~/DOWNLOADS/framework-3.0-beta-3$ ./msfweb 
./script/../config/boot.rb:18:in `require': no such file to load -- rubygems (LoadError)
        from ./script/../config/boot.rb:18
        from script/server:2
chris@ubuntu:~/DOWNLOADS/framework-3.0-beta-3$ apt-cache search ruby gems
chris@ubuntu:~/DOWNLOADS/framework-3.0-beta-3$ 
```

I dont understand how to use metasploit, but I am trying to learn. If I want to test mysql running on my computer, should I do this?

```
chris@ubuntu:~/DOWNLOADS/framework-3.0-beta-3$ ./msfcli auxiliary/scanner/mssql/mssql_login E
Auxiliary failed: The following options failed to validate: RHOSTS.
Backtrace:
./lib/msf/base/simple/auxiliary.rb:54:in `run_simple'
./lib/msf/base/simple/auxiliary.rb:82:in `run_simple'
./msfcli:179

chris@ubuntu:~/DOWNLOADS/framework-3.0-beta-3$ 
```

I put E for the mode. It means Execute. I put auxiliary/scanner/mssql/mssql_login for the exploit name. What am I doing wrong?

---

