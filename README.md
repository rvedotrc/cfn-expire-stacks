cfn-expire-stacks
=================

In AWS CloudFormation, if a stack fails to create, then it rolls back (any
resources it had are deleted), and it goes into `ROLLBACK_COMPLETE` state, so
that its events can be inspected to understand the cause of the failure.  Once
these events are no longer required, the stack can be deleted.  Stacks in
`ROLLBACK_COMPLETE` stay there indefinitely until "DeleteStack" is called.

`cfn-expire-stacks` enumerates stacks in `ROLLBACK_COMPLETE` state, finds
those which are older than (by default) a week, and – assuming their events
are no longer required – deletes each stack thus found.

