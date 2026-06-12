---
title: "[SOLVED] Linux, Bash, and file descriptors"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by cybo on 2008-03-06
I'm writing a bash script (my first one) and I need help (at least as I understood) with file descriptors. Can anyone explain what they are how do they work? I need them so I could save the results of my script to a file. Here are the commands I'm trying to implement in Bash
sstr="blah blah blah"
result=$( find ./ -iname $infile )

and then I want to save sstr and result into another file but I don't know how to do that? Can anyone help.

Please keep in mind I'm now to Linux, Ubuntu, programming, and computers.

---

### Post by dwanders on 2008-03-06
Check this out - it should help you with bash:

[http://tldp.org/LDP/abs/html/io-redirection.html](http://tldp.org/LDP/abs/html/io-redirection.html)

You did not ask for Perl, but here is how it would be done in Perl:

# Write current information to storage file 
open(HSFILE, ">$history_file") or die("Unable to open file");
foreach my $host (@current)
{
    print HSFILE "$host \n";
}
close(HSFILE);

I started doing a bunch of stuff in Bash, and move to Perl for platform portability and found it to be excellently documented - there is not a thing I need to do I cannot Google like Perl arrays, or Perl Open File, or Perl close file etc... 

good luck.

---

### Post by cybo on 2008-03-06
> **dwanders said:**
> Check this out - it should help you with bash:

[http://tldp.org/LDP/abs/html/io-redirection.html](http://tldp.org/LDP/abs/html/io-redirection.html)

You did not ask for Perl, but here is how it would be done in Perl:

# Write current information to storage file 
open(HSFILE, ">$history_file") or die("Unable to open file");
foreach my $host (@current)
{
    print HSFILE "$host \n";
}
close(HSFILE);

I started doing a bunch of stuff in Bash, and move to Perl for platform portability and found it to be excellently documented - there is not a thing I need to do I cannot Google like Perl arrays, or Perl Open File, or Perl close file etc... 

good luck.

Thank you for your help.

---

