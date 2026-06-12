---
title: "Can't remember name of program"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by Kurt` on 2006-08-10
Hi,

There is a simple command line program that you can feed a string of text, or a file, and it outputs it as large text.

e.g.

hello

=

[img]http://xs304.xs.to/xs304/06324/hello1.png[/img]

I can't remember the name of it though. Help me out!

Thanks!

---

### Post by kebes on 2006-08-10
Don't know of a commandline util, but there are online sites to do that. For instance:
[http://www.network-science.de/ascii/](http://www.network-science.de/ascii/)

---

### Post by Kurt` on 2006-08-10
Yeah, I've been to that site before, but never read the FAQ til this morning. Thanks though!

The program in question (that I found in their FAQ about 20 minutes after creating this thread), is 'figlet'.

I just finished writing a perl script for Irssi that uses it. :D

Normally you can just do /exec -msg #channel figlet BLAH to spam large text, but I wanted to make something a little more fun.

# sudo apt-get install figlet

Figlet is in the non-free repositories, [add them to your /etc/apt/sources.list](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

/rh Ubuntu o/ = [http://img149.imageshack.us/img149/8807/ubuntuyu1.png](http://img149.imageshack.us/img149/8807/ubuntuyu1.png)

Here's the script:

```
#!/usr/bin/perl

use Irssi;
use Irssi::Irc;

my @colors = ('0', '4', '8', '9', '11', '12', '13');

# returns random-colored string
sub make_colors {
	my ($string) = @_;
	my $newstr = "";
	my $last = 255;
	my $color = 0;

	my $turn = int(rand(2));

	for (my $c = 0; $c < length($string); $c++) {
		my $char = substr($string, $c, 1);
		if ($char eq ' ') {
			$newstr .= $char;
			next;
		}
		if($turn == 1) {
			$char = uc($char);
			$turn = 0;
		}
		else {
			$char = lc($char);
			$turn = 1;
		}

		while (($color = int(rand(scalar(@colors)))) == $last) {};
		$last = $color;
		$newstr .= "\003";
		$newstr .= sprintf("%02d", $colors[$color]);
		$newstr .= (($char eq ",") ? ",," : $char);
	}

	return $newstr;
}

sub rh {
	my ($text, $server, $dest) = @_;

	if (!$server || !$server->{connected}) {
		Irssi::print("Not connected to server");
		return;
	}
	
	return unless $dest;
	
	if ($dest->{type} eq "CHANNEL" || $dest->{type} eq "QUERY") {
		my @result = `figlet $text`;
		foreach $temp (@result) {
			if($temp eq "\n") { next; }
			$temp =~ s/(.+)\n/\1/;
			$dest->command("/msg " . $dest->{name} . " " . make_colors($temp));
		}
	}
}

Irssi::command_bind("rh", "rh");
```
RH = rainbow huge, feel free to rename it.

Text passed to the script is not sanitized, do not use && or || or |, or anything that can seperate commands in your text.

Save it to a .pl file in ~/.irssi/scripts, or ~/.irssi/scripts/autorun (for it to load when irssi starts), then /script load it, and type /rh text.

---

### Post by steve.horsley on 2006-08-10
man banner

---

### Post by Kurt` on 2006-08-11
> **steve.horsley said:**
> man banner

I already knew about banner, and it's not what I wanted. Thanks anyways though :)

---

