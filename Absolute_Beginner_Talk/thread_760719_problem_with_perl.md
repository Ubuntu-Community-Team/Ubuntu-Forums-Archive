---
title: "problem with perl"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by yiddski on 2008-04-20
Missing base argument at /usr/share/perl5/HTTP/Response.pm line 93

i get that when i try to run this 
```


use WWW::Mechanize

my $url = 'http://lulznw.com/';
my $mech = WWW::Mechanize->new(autocheck=>1);
my $username = 'username';
my $password = 'password';
my $message = <<message

message

;
$mech->get( $url );
$target = $mech->content;
$mech->form_name('maintable');
$mech->field('username',$username);
$mech->field('password',$password);
$mech->click();

```

---

### Post by KingTermite on 2008-06-11
Sounds like an error in a module being used.

---

