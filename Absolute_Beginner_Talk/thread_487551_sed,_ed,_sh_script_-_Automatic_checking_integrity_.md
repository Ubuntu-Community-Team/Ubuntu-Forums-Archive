---
title: "sed, ed, sh script - Automatic checking integrity of a text file"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Carlos Santiago on 2007-06-29
I would like to check the integrity of my bibtex file that has more than 1400 entries.

The problem is that many of those entries are wrong entries, and I would like to identify and remove them.

Please see the following example

```
@misc{abella2004lbs,
  title={{Libro blanco del software libre en Espa{\~n}a}},
  author={ABELLA, A. and SANCHEZ, J. and SEGOVIA, MA},
  year={2004},
  publisher={Extremadura},
  pdf={_Papers_Geral/@abella2004lbs - libro_blanco_del_software_libre.pdf}
}

@article{gerdtham2000ich,
  title={{International Comparisons of Health Expenditure: Theory, Data and Econometric Analysis}},
  author={Gerdtham, U.G. and J{\"o}nsson, B.},
  journal={Handbook of Health Economics},
  volume={1},
  pages={11--53},
  year={2000},
  publisher={Elsevier},
  pdf={e-Books/Wiley.Ubuntu.Linux.Bible/@gerdtham2000ich - Wiley.Ubuntu.Linux.Bible-Chapter.01-The.Ubuntu.Linux.Project.pdf}
}

```

In the example the 'abella2004lbs' entry is OK, but the 'gerdtham2000ich' is wrong.

What I want to do  is to make a script that checks if the first 2 or 3 words of the title exists in the pdf filename.

If found, save the entry to a file named 'confirmed_entries'.

If not, save the entry to a file named 'removed_entries'.

Thanks for any help

Regards,

Carlos

---

### Post by bartonski on 2007-07-07
Here is a quick perl script which will do most of the work for you, this will split the sections out, and figure out whether words in the title match words in the pdf section.

This code is by no means robust, but it should get you most of the way to where you want to go.

```

#! /usr/bin/perl -w

use strict;

# Create an array of sections
my @sections;
my $temp_array;

while(<>){
        if(/^@/){
                $temp_array = [];
                push @$temp_array, $_;
        } elsif (/^}/) {
                push @$temp_array, $_;
                push @sections, $temp_array;
        } else {
                push @$temp_array, $_;
        }
}

# Analyze section
my $section_number = 1;
my $section;
for $section (@sections) {
        print "Section number $section_number\n";
        print @$section;
        $section_number++;
        my @title_words;
        my $match_count = 0;
        my $line;
        for $line (@$section){
                if($line =~ /title=\{\{(.+)\}\}/){
                        @title_words = split /\s/, $1;
                }
                if($line =~ /pdf=\{(.+)\}/){
                        my $pdf_contents = $1;
                        my $word;
                        for $word (@title_words){
                                $match_count++ if ( $pdf_contents =~ /$word/);
                        }
                }
        }
        print "Section is correct\n" if ($match_count);
}

```

---

### Post by Carlos Santiago on 2007-07-07
Thanx bartonski,

---

### Post by KIAaze on 2007-07-18
I created a bash shellscript which uses the previous perl script but also stores the correct entries in "confirmed_entries" and the incorrect ones in "removed_entries". :)
The output of the perl script itself is stored in "all.log".
The names of those three logfiles can be changed by modifying the lines 17,18,19 accordingly.

```

#! /bin/bash
# This shellscript checks the integrity of bibtex files by comparing the title name with the pdf name.

# Check if all parameters are present
# If no, exit
if [ $# -ne 1 ]
then
	echo
        echo "This shellscript checks the integrity of bibtex files by comparing the title name with the pdf name."
	echo "usage :"
	echo "$0 [file]"
	echo
	exit 0 
fi

#You can change the names of the logfiles here as you wish:
OK_LOG="confirmed_entries"
NOT_OK_LOG="removed_entries"
ALL_LOG="all.log"

#remove previous logfiles
rm -f $OK_LOG $NOT_OK_LOG

#create a file containing the output of the perl script
perl -x $0 $1 >$ALL_LOG

#get line numbers of "Section number" parts
line_nb=`grep -n "Section number" $ALL_LOG | cut -f1 -d:`
#get number of the last line
last_line=`cat $ALL_LOG | wc -l`

#initialize variables
prev_section=1
count_ok=0
count_not_ok=0

#treat sections
for section in $line_nb
do
  prev_section_end=`expr $section - 1`
  if [ $section -ne "1" ]
  then
    echo $prev_section_start to $prev_section_end
    diagnostic=`sed -n "$prev_section_end,$prev_section_end p" $ALL_LOG`
    if [ "$diagnostic" == "Section is correct" ]
    then
      echo OK
      start=`expr $prev_section_start + 1`
      end=`expr $prev_section_end - 1`
      sed -n "$start,$end p" $ALL_LOG >>$OK_LOG
      count_ok=`expr $count_ok + 1`
      echo "==============="
    else
      echo not OK
      start=`expr $prev_section_start + 1`
      end=`expr $prev_section_end`
      sed -n "$start,$end p" $ALL_LOG >>$NOT_OK_LOG
      count_not_ok=`expr $count_not_ok + 1`
      echo "==============="
    fi
  fi
  prev_section_start=$section
done

#treat last section
echo $prev_section_start to $last_line
diagnostic=`sed -n "$last_line,$last_line p" $ALL_LOG`
if [ "$diagnostic" == "Section is correct" ]
then
  echo OK
  start=`expr $prev_section_start + 1`
  end=`expr $last_line - 1`
  sed -n "$start,$end p" $ALL_LOG >>$OK_LOG
  count_ok=`expr $count_ok + 1`
  echo "==============="
else
  echo not OK
  start=`expr $prev_section_start + 1`
  end=`expr $last_line`
  sed -n "$start,$end p" $ALL_LOG >>$NOT_OK_LOG
  count_not_ok=`expr $count_not_ok + 1`
  echo "==============="
fi

#calculate total nb of sections
count_total=`expr $count_ok + $count_not_ok`

#end summary
echo "Number of sections that are OK: $count_ok"
echo "Number of sections that are not OK: $count_not_ok"
echo "Total number of sections processed: $count_total"
echo
echo "Complete perl script output in: $ALL_LOG"
echo "OK sections stored in: $OK_LOG"
echo "not OK sections stored in: $NOT_OK_LOG"

#exit to avoid perl script
exit 0

# =======================================================
#Perl script created by bartonski

#! /usr/bin/perl -w

use strict;

# Create an array of sections
my @sections;
my $temp_array;

while(<>){
        if(/^@/){
                $temp_array = [];
                push @$temp_array, $_;
        } elsif (/^}/) {
                push @$temp_array, $_;
                push @sections, $temp_array;
        } else {
                push @$temp_array, $_;
        }
}

# Analyze section
my $section_number = 1;
my $section;
for $section (@sections) {
        print "Section number $section_number\n";
        print @$section;
        $section_number++;
        my @title_words;
        my $match_count = 0;
        my $line;
        for $line (@$section){
                if($line =~ /title=\{\{(.+)\}\}/){
                        @title_words = split /\s/, $1;
                }
                if($line =~ /pdf=\{(.+)\}/){
                        my $pdf_contents = $1;
                        my $word;
                        for $word (@title_words){
                                $match_count++ if ( $pdf_contents =~ /$word/);
                        }
                }
        }
        print "Section is correct\n" if ($match_count);
}


```

---

### Post by Carlos Santiago on 2007-07-18
Thanx KIAaze,
Nice post!

---

