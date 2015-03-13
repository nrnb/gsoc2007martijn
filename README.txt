Google Summer of Code 2007
GenMAPP Project
Martijn van Iersel

These are diff files for all the code I wrote during the Google Summer of Code 2007 for the GenMAPP Project. These diffs are generated directly from the subversion repository using the perl script below.

All code is licensed under the Apache 2.0 License

Note that the diffs by itself don't make a working program. To compile a running program you can find the complete source repository at http://svn.bigcat.unimaas.nl/pathvisio/

At the time of this writing there is a prototype running online at http://blog.bigcat.unimaas.nl/~martijn/wikipathways/listing.php. The plan is that this work will get integrated into the site http://www.wikipathways.org


---------- Script to obtain diffs --------------

#!/usr/bin/perl

use warnings;
use strict;

my @lines = `svn log -r908:1146 -q http://svn.bigcat.unimaas.nl/pathvisio`;

for my $line (@lines)
{
	if ($line =~ /^r(\d+)\W+(\w+)/)
	{
		my $rev = $1;
		my $revbefore = $rev - 1;
		my $person = $2;
		my $fnOut = "${person}_r${rev}_diff.txt";
		system ("svn diff -r${revbefore}:${rev} http://svn.bigcat.unimaas.nl/pathvisio > $fnOut");
		print "Wrote $fnOut\n";
	}
}

<STDIN>;
