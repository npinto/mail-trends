# mail-trends

## Overview
Mail Trends lets you analyze and visualize your email (as extracted from an IMAP server). You can see:

* Distribution of messages by year, month, day, day of week and time of day
* Distribution of messages by size and your top 40 largest messages
* The top senders, recipients and mailing lists you're on.
* Distributions of senders, recipients and mailing lists over time
* The distribution of thread lengths and the lists and people that result in the longest threads

## Getting Started
### Requirements
* A Gmail or Google Apps mail account
* Python 2.5 or later

### Installation
You will need [Cheetah](http://www.cheetahtemplate.org/) (a template system) installed. You can [download](http://pypi.python.org/packages/source/C/Cheetah/Cheetah-2.4.4.tar.gz) it and then follow the [installation instructions](http://www.cheetahtemplate.org/docs/users_guide_html_multipage/gettingStarted.install.html). If you are using an apt-based Linux distribution sudo apt-get install python-cheetah may be enough for you.

### Running
From within the mail-trends directory run the following, replacing the username and passwords as appropriate (if you omit the password in the commandline you will be (securely) prompted for it):

    python main.py \
      --server=imap.gmail.com \
      --use_ssl \
      --username=username@gmail.com \
      --me=username@gmail.com,username@somedomain.com \
      --skip_labels

You will be prompted for the password for your account (you can also use --password= to specify it as an argument. The --me argument lets you specify what emails should be considered as being sent to/from you.

The output is in HTML, placed in out/index.html. Open that in your favorite web browser.

### Other options
--skip_labels does not categorize messages into labels (there are not stats that use them yet).

--filter_out=... can be used to ignore certain messages. You can use to:username@example.com, from:username@example.com or list:listid.example.com to filter out by recipient, sender or list (you can have multiple filter clauses by separating them with commas).

You can pass in --record and --replay as command line arguments to respectively capture and play black message fetches from the IMAP server. This is meant to aid in development by speeding up data fetches.

--max_messages=NNNN can be used to limit the number of messages that are fetched. Normally the most recent messages are selected, use --random_subset to specify that the messages be chosen over all the messages.

--days=NNNN Fetch mail from last NNNN days. If NNNN is omitted then it defaults to all days until the Unix epoch (effectively all mail)

--date_from Fetches mail from date until the the end of the dataset. Format: %d-%b-%Y

Examples:

Fetch mail from last 10 days:
--days=10
Fetch all mail between a certain date and the end of the dataset:
--date_from=12-Apr-2012
Fetch all mail from a certain date until 10 days earlier:
--date_from=12-Apr-2012 --day=10

## History
Original project hosted at [http://code.google.com/p/mail-trends/](http://code.google.com/p/mail-trends/)
