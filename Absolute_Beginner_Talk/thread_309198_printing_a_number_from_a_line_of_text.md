---
title: "printing a number from a line of text?"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by meniscus on 2006-11-29
Im trying to write a command thatll return just the CPU temperature

Ive got this so far

```
meniscus@meniscot:~$ sensors | grep 'CPU Temp'
CPU Temp:    +43°C  (low  =   +15°C, high =   +45°C)   sensor = diode
```


How do i modify it to take out just the number 43?

---

### Post by Bachstelze on 2006-11-29
You could do that with with *head* and *tail*, cutting the appropriate number of bytes. There might be a more elegant way dut I don't know it :p

---

### Post by meniscus on 2006-11-29
Tanks, i got this line

```
meniscus@meniscot:~$ sensors | grep 'CPU Temp' | head -c 16 | tail -c 2
42meniscus@meniscot:~$

```


If i assigned this line to a variable in a perl script would it work?

ie

```
#Getting temperature and assign to variable my $temp
my $temp=`/usr/bin/sensors | grep 'CPU Temp' | head -c 16 | tail -c 2`;
	
# remove eol chars and white space
	$temp =~ s/[\n ]//g;

```

Would that be ok?

---

### Post by Arndt on 2006-11-29
> **meniscus said:**
> Tanks, i got this line

```
meniscus@meniscot:~$ sensors | grep 'CPU Temp' | head -c 16 | tail -c 2
42meniscus@meniscot:~$

```


If i assigned this line to a variable in a perl script would it work?

ie

```
#Getting temperature and assign to variable my $temp
my $temp=`/usr/bin/sensors | grep 'CPU Temp' | head -c 16 | tail -c 2`;
	
# remove eol chars and white space
	$temp =~ s/[\n ]//g;

```

Would that be ok?

Since you're already in Perl, it's much better to use its matching facilities. Something like

```
my $temp=`/usr/bin/sensors | grep 'CPU Temp'`;

$temp =~ /([+0-9-]+)/
$temp = $1
```

(Untested, except for the regular expression itself.) Maybe you want error handling too. What happens if there is no such line in the input?

---

