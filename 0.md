
### Выгрузить все pseudo_user_id за день и подтянуть к ним user_id
~~~sql
select distinct(t.user_pseudo_id), u.id
from `beaming-storm-315705.Test.TestEvent` as t
left join (select table.user_pseudo_id, params.key, params.value.int_value as id
    from `beaming-storm-315705.Test.TestEvent` as table,
    table.event_params as params
    where key = 'UserID') as u using(user_pseudo_id)
~~~
