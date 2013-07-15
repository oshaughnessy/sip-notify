sip-notify
==========

This script tells a SIP user that they have new Asterisk voicemail by
changing the status of their phone's message waiting indicator.


## Usage

    sip-notify:  control state of a SIP client's message waiting indicator (MWI)

    Usage:
         sip-notify [<opts>] --new <# msgs> --old <# msgs> <sip address>
      or sip-notify [<opts>] <context> <sip address> <# msgs>
      or sip-notify [<opts>] --all

    Options:
      --help        Show this usage text.
      --man         Show the comprehensive documentation.
      --verbose|-v  Show details of progress (give more than once for more info).
      --version     Show the version (0.1.10).
      --db          Update the voicemail status database with the user's number
                    of old and new messages.
      --new #       The number of new voicemail messages waiting for the recipient.
      --old #       The number of old voicemail messages waiting for the recipient.
      --all         Send a SIP NOTIFY message to every user who has subscribed
                    to their voicemail updates.

    The second form of usage is designed to allow sip-notify to be called
    from the Asterisk PBX voicemail module, as an "externnotify" command.
    (See www.asterisk.org.)  The MWI state is figured out based on the number
    of message files the mailbox has in the Asterisk spool (the location of
    which is partly determined by the given context).

    In the third form of usage, every SIP user that has subscribed to voicemail
    notifications will be sent a NOTIFY message with the current status of their
    voicemail.


## Install

This script requires a small bit of customization.  Look for "CHANGEME"
in sip-notify to set the sipsak proxy and the default SIP domain.


## Requirements

This script forms a SIP message and sends it using
[sipsak](http://www.sipsak.org).


## License

This code is licensed under the Perl Artistic License, version 2.0.  For
more information, please see the file Artistic_2.0, which was included with
this distribution, or http://opensource.org/licenses/artistic-license-2.0.php
