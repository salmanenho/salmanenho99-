create table if not exists public.entries (
  id bigint generated always as identity primary key,
  section text not null,
  field1 text,
  field2 text,
  created_at timestamp with time zone default now()
);

-- تأكد من أن جميع المستخدمين يمكنهم الإدخال (API)
-- (للبيئة التجريبية فقط — لاحقاً يجب ضبط صلاحيات الأمان)
alter table public.entries enable row level security;

create policy \"Allow insert for all\" on public.entries
  for insert
  with check (true);
