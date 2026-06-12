---
title: "[SOLVED] conky and POP mail"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by il-luzhin on 2007-05-22
Can someone help me with this last little bit of conky code trouble please?

This
```

gedit /home/luzhin/.conkyrc

```
gets me this portion of the conf file
```

${color #e9c703}Inbox
$color${texeci 600 /home/luzhin/scripts/email.pl}

```
which leads to this 
```

#!/usr/bin/perl

# beginning of configuration

# pop3 host
$pop_host = "**pop_server**";

# pop3 username 
$pop_user = "**usr_name**";

# pop3 password
$pop_pass = "**password**";

# ssl port number
$ssl_port = "995";

# ssl protocol
$ssl_prot = "tcp";

# number of emails to show
$dis_numb = "5";

# end of configuration

use Mail::POP3Client;
use IO::Socket::SSL;

  my $socket = IO::Socket::SSL->new( PeerAddr => $pop_host,
                                     PeerPort => $ssl_port,
                                     Proto    => $ssl_prot);
  my $pop = Mail::POP3Client->new();
  $pop->User($pop_user);
  $pop->Pass($pop_pass);
  $pop->Socket($socket);
  $pop->Connect();

$msg_count = $pop->Count();

for ($i = $msg_count, $j = 0; $i >= $msg_count-($dis_numb-1); $i--, $j++) {
  foreach ( $pop->Head( $i ) ) {
    #/^(From|Subject):\s+/i and print $_, "\n";
    if ($_ =~ m/^From:/) {
      ($from) = ($_ =~ m#^From: .*<(.*)>#);
      $from = substr($from, 0, 30);
      $out .= "$j = $from\n";
    }
  }
  #chop $out;
  `echo -e "$out"> ~/.gmail/.gmail_top`;
}

$pop->Close();

```

Thnx

---

### Post by diatribe on 2007-05-22
so...are you looking for a working conky gmail script?

---

### Post by il-luzhin on 2007-05-22
not gmail.  Trying to setup just a pop mail account

---

### Post by justleen on 2007-05-22
and what is not working? (the scripy you have is for gmaill..)

check [http://ubuntuforums.org/showthread.php?p=2628010](http://ubuntuforums.org/showthread.php?p=2628010)

---

### Post by il-luzhin on 2007-05-22
thnx

---

