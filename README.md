Minimum viable test project for https://code.djangoproject.com/ticket/35424

This is based on the polls demo app from the django docs: https://docs.djangoproject.com/en/4.2/intro/tutorial01/

The deviation is changing the `polls.Choice` model to have `order_with_respect_to = "question"`, then removing it in favour of an explicit `_order = models.IntegerField()` field. This causes django's migration autodetector to follow a code path that results in a crash due to an invalid field lookup.
