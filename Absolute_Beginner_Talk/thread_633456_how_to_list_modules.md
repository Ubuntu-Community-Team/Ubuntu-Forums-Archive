---
title: "how to list modules"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by HurricaneDan on 2007-12-06
I am looking for a way to see which perl modules are installed on my machine.  Is there a way to find modules for portion of the linux install?

Thanks,

Dan

---

### Post by camccall on 2007-12-06
Okay, so I found this [here]("http://www.cpan.org/misc/cpan-faq.html").  Can't test at work so I am not sure if it will give you exactly what you are looking for.  Just drop this into a perl script and run and you should get a list. 

```

#!/usr/local/bin/perl

use ExtUtils::Installed;
my $instmod = ExtUtils::Installed->new();
foreach my $module ($instmod->modules()) {
my $version = $instmod->version($module) || "???";
       print "$module -- $version\n";
}

```

---

### Post by HurricaneDan on 2007-12-07
Thanks that is what I needed.

If anyone else comes across this though I will add one more thing that I did not realize going in to this.  On my server this pl file had to be in the cgi-bin directory as this directory allows for the execution of the script.

So I actually learned two things from this.

Thanks

---

